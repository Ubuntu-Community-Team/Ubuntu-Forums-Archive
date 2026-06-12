---
title: "iMac and wake from sleep radeon issues"
date: 2020-07-25
forum: Apple Hardware Users
---

### Post by DigiAngel on 2020-07-25
Well...ever since 20 anytime I wake the device from sleep I see the below in dmesg (ssh'd in):
```
[42197.747777] radeon 0000:01:00.0: GPU lockup (current fence id 0x00000000000fb78a last fence id 0x00000000000fb7ab on ring 0)
[42198.058608] radeon 0000:01:00.0: Saved 1177 dwords of commands on ring 0.
[42198.058617] radeon 0000:01:00.0: GPU softreset: 0x00000009
[42198.058619] radeon 0000:01:00.0:   R_008010_GRBM_STATUS      = 0xE4703030
[42198.058621] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2     = 0x00110103
[42198.058623] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS      = 0x200000C0
[42198.058625] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[42198.058626] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00008002
[42198.058628] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00008086
[42198.058630] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80018645
[42198.058632] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[42198.111206] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00007FEF
[42198.111259] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000100
[42198.113347] radeon 0000:01:00.0:   R_008010_GRBM_STATUS      = 0xA0003030
[42198.113349] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2     = 0x00000003
[42198.113351] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS      = 0x200080C0
[42198.113352] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[42198.113354] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[42198.113356] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[42198.113358] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80100000
[42198.113360] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[42198.113366] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
[42198.904136] [drm] PCIE GART of 512M enabled (table at 0x0000000000142000).
[42198.904159] radeon 0000:01:00.0: WB enabled
[42198.904163] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000008000c00 and cpu addr 0x00000000ad0cde26
[42198.904584] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x00000000000521d0 and cpu addr 0x00000000aee699e6
```

After issuing a "sudo reboot", I'm finished...device will have to be hard reset in order to use it.  Anyone know of how to change the driver for the radeon card on linux?  Device is Advanced Micro Devices, Inc. [AMD/ATI] RV610/M74 [Mobility Radeon HD 2400 XT].  Thanks.

---

