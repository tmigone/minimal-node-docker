# Minimal docker images with nodejs runtime

This repo is to test what a minimal docker image with nodejs runtime looks like.


## Results

```
[Info]               ┌───────────────────┬────────────┬───────────────────────┐
[Info]               │ Service           │ Image Size │ Build Time            │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ entware           │ 12.45 MB   │ 1 minute, 8 seconds   │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ entware-node      │ 39.84 MB   │ 2 minutes, 27 seconds │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ busybox           │ 153.27 MB  │ 5 minutes, 31 seconds │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ alpine            │ 482.68 MB  │ 2 minutes, 20 seconds │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ alpine-node-build │ 587.37 MB  │ 3 minutes, 5 seconds  │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ alpine-node-run   │ 146.75 MB  │ 2 minutes, 48 seconds │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ node              │ 111.36 MB  │ 1 minute, 2 seconds   │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ caxa              │ 512.83 MB  │ 6 minutes, 9 seconds  │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ pkg               │ 774.04 MB  │ 7 minutes, 48 seconds │
[Info]               ├───────────────────┼────────────┼───────────────────────┤
[Info]               │ dockerize         │ 76.37 MB   │ 1 minute, 10 seconds  │
[Info]               └───────────────────┴────────────┴───────────────────────┘
```

Some observations:
- When using `balenalib` base images `BALENA_ARCH` images result in smaller images when compared to `BALENA_MACHINE_NAME` images
- Best current result is:
  - For `aarch64` use `entware + opkg` --> ~40MB image size
  - For generic arch use:
    - `node` --> ~110MB image size
    - `dockerize`--> ~76MB image size

