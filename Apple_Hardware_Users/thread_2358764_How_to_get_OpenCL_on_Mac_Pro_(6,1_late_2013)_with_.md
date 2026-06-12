---
title: "How to get OpenCL on Mac Pro (6,1 late 2013) with Ubuntu 17.04?"
date: 2017-04-17
forum: Apple Hardware Users
---

### Post by pdaliu2 on 2017-04-17
Hi all:
  With the newly released amdgpu driver, I'd like to install 17.04 server on a headless Mac Pro (6,1 late 2013, 64GB RAM with AMD D700 6GB x 2).  I have managed to boot successfully into the system.  In addition to fixing the EFI partition, I also activated iommu and blacklisted apple_gmux because both D700 would only be used for OpenCL (hopefully).  Some excerpts from dmesg are listed below <List 2>.  I followed Laanwj's instructions ([https://laanwj.github.io/2016/05/06/opencl-ubuntu1604.html](https://laanwj.github.io/2016/05/06/opencl-ubuntu1604.html)) and installed libclc-amdgcn + mesa-opencl-icd.  However, the output of clinfo is on <List 1>.  My questions:

1. Seemed one GPU was bound to radeon, and the other was to amdgpu.  I expected to see at least one CPU device and one GPU device (not counting the radeon-bound one).  How come there's none?

2. Can I bind both GPUs to amdgpu?  Hopefully then I can get two GPU devices.


Any tips could be helpful.  Thanks in advance!!

Regards,

pdaliu

<List 1>
Number of platforms                               1
  Platform Name                                   Clover
  Platform Vendor                                 Mesa
  Platform Version                                OpenCL 1.1 Mesa 17.1.0-devel - padoka PPA
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd
  Platform Extensions function suffix             MESA


  Platform Name                                   Clover
Number of devices                                 0


NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  Clover
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   Clover
  clCreateContext(NULL, ...) [default]            No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No devices found in platform


ICD loader properties
  ICD loader Name                                 OpenCL ICD Loader
  ICD loader Vendor                               OCL Icd free software
  ICD loader Version                              2.2.11
  ICD loader Profile                              OpenCL 2.1


<List 2>
[    0.426132] pci 0000:02:00.0: vgaarb: VGA device added: decodes=io+mem,owns=none,locks=none
[    0.426137] pci 0000:06:00.0: vgaarb: VGA device added: decodes=io+mem,owns=none,locks=none
[    0.426142] pci 0000:06:00.0: vgaarb: setting as boot device
[    0.426144] pci 0000:06:00.0: vgaarb: bridge control possible
[    0.426147] pci 0000:02:00.0: vgaarb: bridge control possible
[    0.426149] vgaarb: loaded

[    1.201561] efifb: probing for efifb
[    1.201577] efifb: framebuffer at 0x90180000, using 8128k, total 8128k
[    1.201580] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    1.201582] efifb: scrolling: redraw
[    1.201584] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0


[    1.722774] [drm] radeon kernel modesetting enabled.

[    1.731175] fb: switching to radeondrmfb from EFI VGA

[    1.732321] radeon 0000:06:00.0: VRAM: 6144M 0x0000000000000000 - 0x000000017FFFFFFF (6144M used)
[    1.732325] radeon 0000:06:00.0: GTT: 2048M 0x0000000180000000 - 0x00000001FFFFFFFF

[    1.732395] [drm] radeon: 6144M of VRAM memory ready
[    1.732397] [drm] radeon: 2048M of GTT memory ready.

[    1.737899] [drm] radeon: dpm initialized

[    1.753976] radeon 0000:06:00.0: WB enabled
[    1.753979] radeon 0000:06:00.0: fence driver on ring 0 use gpu addr 0x0000000180000c00 and cpu addr 0xffff8de86b075c00
[    1.753984] radeon 0000:06:00.0: fence driver on ring 1 use gpu addr 0x0000000180000c04 and cpu addr 0xffff8de86b075c04
[    1.753988] radeon 0000:06:00.0: fence driver on ring 2 use gpu addr 0x0000000180000c08 and cpu addr 0xffff8de86b075c08
[    1.753992] radeon 0000:06:00.0: fence driver on ring 3 use gpu addr 0x0000000180000c0c and cpu addr 0xffff8de86b075c0c
[    1.753996] radeon 0000:06:00.0: fence driver on ring 4 use gpu addr 0x0000000180000c10 and cpu addr 0xffff8de86b075c10
[    1.754153] radeon 0000:06:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffaacc88035a18

[    1.774164] radeon 0000:06:00.0: fence driver on ring 6 use gpu addr 0x0000000180000c18 and cpu addr 0xffff8de86b075c18
[    1.774168] radeon 0000:06:00.0: fence driver on ring 7 use gpu addr 0x0000000180000c1c and cpu addr 0xffff8de86b075c1c
[    1.774173] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.774175] [drm] Driver supports precise vblank timestamp query.
[    1.774178] radeon 0000:06:00.0: radeon: MSI limited to 32-bit
[    1.774207] radeon 0000:06:00.0: radeon: using MSI.
[    1.774225] [drm] radeon: irq initialized.

[    4.143313] fbcon: radeondrmfb (fb0) is primary device
[    4.167635] Console: switching to colour frame buffer device 240x67
[    4.170409] radeon 0000:06:00.0: fb0: radeondrmfb frame buffer device
[    4.186156] [drm] Initialized radeon 2.49.0 20080528 for 0000:06:00.0 on minor 0





[    4.197775] [drm] amdgpu kernel modesetting enabled.
[    4.197905] amdgpu 0000:02:00.0: enabling device (0006 -> 0007)
[    4.198045] [drm] initializing kernel modesetting (TAHITI 0x1002:0x6798 0x106B:0x0128 0x00).
[    4.198115] [drm] register mmio base: 0xA0700000
[    4.198127] [drm] register mmio size: 262144
[    4.198150] [drm] ACPI VFCT contains a BIOS for 02:00.0 1002:6798, size 65536
[    4.198177] ATOM BIOS: Tahiti
[    4.198189] [drm] GPU post is not needed
[    4.198199] [drm] Changing default dispclk from 500Mhz to 600Mhz
[    4.198463] amdgpu 0000:02:00.0: VRAM: 6144M 0x0000000000000000 - 0x000000017FFFFFFF (6144M used)
[    4.198521] amdgpu 0000:02:00.0: GTT: 6144M 0x0000000180000000 - 0x00000002FFFFFFFF
[    4.198542] [drm] Detected VRAM RAM=6144M, BAR=256M
[    4.198555] [drm] RAM width 384bits GDDR5
[    4.198574] [drm] amdgpu: 6144M of VRAM memory ready
[    4.198588] [drm] amdgpu: 6144M of GTT memory ready.
[    4.198605] [drm] GART: num cpu pages 1572864, num gpu pages 1572864
[    4.200329] amdgpu 0000:02:00.0: PCIE GART of 6144M enabled (table at 0x0000000000040000).
[    4.200400] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.200416] [drm] Driver supports precise vblank timestamp query.
[    4.200451] amdgpu 0000:02:00.0: amdgpu: using MSI.
[    4.200474] [drm] amdgpu: irq initialized.
[    4.200491] [drm] probing gen 2 caps for device 8086:e04 = 27a7d03/e
[    4.200518] [drm] Internal thermal controller with fan control
[    4.200537] [drm] amdgpu: dpm initialized

[    4.218634] amdgpu 0000:02:00.0: fence driver on ring 0 use gpu addr 0x0000000180000010, cpu addr 0xffff8de86c22d010
[    4.219476] amdgpu 0000:02:00.0: fence driver on ring 1 use gpu addr 0x0000000180000020, cpu addr 0xffff8de86c22d020
[    4.220308] amdgpu 0000:02:00.0: fence driver on ring 2 use gpu addr 0x0000000180000030, cpu addr 0xffff8de86c22d030
[    4.221137] amdgpu 0000:02:00.0: fence driver on ring 3 use gpu addr 0x0000000180000040, cpu addr 0xffff8de86c22d040
[    4.221948] amdgpu 0000:02:00.0: fence driver on ring 4 use gpu addr 0x0000000180000050, cpu addr 0xffff8de86c22d050

[    4.550294] amdgpu 0000:02:00.0: fb1: amdgpudrmfb frame buffer device
[    4.551138] [drm] ib test on ring 0 succeeded
[    4.551917] [drm] ib test on ring 1 succeeded
[    4.552642] [drm] ib test on ring 2 succeeded
[    4.553353] [drm] ib test on ring 3 succeeded
[    4.554060] [drm] ib test on ring 4 succeeded
[    4.841211] [drm] Initialized amdgpu 3.9.0 20150101 for 0000:02:00.0 on minor 1

---

