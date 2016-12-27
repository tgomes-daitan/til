# til
Today I learned


# Flamegraphs

Generating a flame graph for the sleep command:

```bash
git clone https://github.com/brendangregg/FlameGraph
sudo sysctl kernel.kptr_restrict=0
sudo sysctl kernel.perf_event_paranoid=0
perf record -F 99 -a -g -- sleep 60
perf script > out.perf
FlameGraph/stackcollapse-perf.pl out.perf > out.folded
FlameGraph/flamegraph.pl out.folded > sleep.svg
```

# Sum the size of some files
```bash
find /directory/ -name some-filter* -exec du {} \; | awk '{s+=$1} END {print s/1024}'
```
