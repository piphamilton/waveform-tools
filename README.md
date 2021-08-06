# Tools for extracting waveforms from DUNE MC

## Contents

### `extract_larsoft_waveforms.cxx`

Extracts waveforms from a non-zero-suppressed DUNE MC file using
[http://art.fnal.gov/gallery](gallery). If you're on a machine with CVMFS mounted (eg Fermilab GPVM or lxplus), `source setup.sh` should set up everything you'll need.

The software is built using `cmake`, so eg:

```shell
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo ..
make
```

Output is to text file or numpy format (using
[https://github.com/rogersce/cnpy](cnpy)). See
`extract_larsoft_waveforms --help` for options, and see the source for
a description of the output format.

The waveforms are accessed through an input tag with the format: [module label]:[product instance name]:[process name] (as returned by eventdump).

### `extract_larsoft_hits.cxx`

Extracts hits from a larsoft file into a flat text file, much like `extract_larsoft_waveforms` does for raw data.

### `read_samples.h`

Contains functions to read the output from `extract_larsoft_waveforms.cxx` (in text or numpy format) back into C++

### `python/protodune/self-trigger-evt-disp.py`

A simple python raw data event display that uses numpy files as created by `extract_larsoft_waveforms`
