# Tarantool

Tarantool can be used in OLTP scenarios instead of relational databases, and
such a solution will work many times faster. With Tarantool, you can replace the
traditional bundle of database & cache and benefit from that by reducing
operational costs.

## Build Docker

    $ sudo docker build -t oss-sydr-fuzz-tarantool .

## Run Hybrid Fuzzing

Unzip Sydr (`sydr.zip`) in `projects/tarantool` directory:

    $ unzip sydr.zip

Run docker:

    $ sudo docker run --privileged --network host -v /etc/localtime:/etc/localtime:ro --rm -it -v $PWD:/fuzz oss-sydr-fuzz-tarantool /bin/bash

Change directory to `/fuzz`:

    # cd /fuzz

Run hybrid fuzzing:

    # sydr-fuzz -c uri.toml run

Collect and report coverage:

    # sydr-fuzz -c uri.toml cov-report

## Hybrid Fuzzing with AFL++

    # sydr-fuzz -c uri-afl++.toml run

## Alternative Fuzz Targets

Tarantool project has 8 fuzz targets.

### csv

    # sydr-fuzz -c csv.toml run
    
### datetime_parse_full

    # sydr-fuzz -c datetime_parse_full.toml run
    
### datetime_strptime

    # sydr-fuzz -c datetime_strptime.toml run

### http_parser

    # sydr-fuzz -c http_parser.toml run
    
### mp_datetime

    # sydr-fuzz -c mp_datetime.toml run

### uri

    # sydr-fuzz -c uri.toml run

### swim_proto_member

    # sydr-fuzz -c swim_proto_member.toml run

### swim_proto_meta

    # sydr-fuzz -c swim_proto_meta.toml run
