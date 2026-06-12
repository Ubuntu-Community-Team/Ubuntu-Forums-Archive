---
title: "Nvidia Geoforce 8600M on Ubuntu 15.04 won't start (MacBookPro 4,1)"
date: 2015-04-25
forum: Apple Hardware Users
---

### Post by kmand on 2015-04-25
My MacbookPro 4,1 with Nvidia Geoforce 8600M worked fine under Ubuntu 14.10. I did the upgrade to 15.04 and couldn't get a desktop. I got the popup about couldn't configure.

I saw a posting suggesting I should get the latest Nvidia driver with legacy support which was Nvidia 340.76 (from xorg-edgers/ppa). It installed without error, but now when I boot I get a momentary console login, replaced by a black screen with a blinking cursor. Control Alt-F1 does not work, but I can ssh in.

The Xorg log shows:

(EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0

The syslog shows:

Apr 24 11:41:47 km-MacBookPro kernel: [   15.519938] nvidia: module license 'NVIDIA' taints kernel.
Apr 24 11:41:47 km-MacBookPro kernel: [   15.519944] Disabling lock debugging due to kernel taint
Apr 24 11:41:47 km-MacBookPro kernel: [   15.532749] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Apr 24 11:41:47 km-MacBookPro kernel: [   15.539207] nvidia 0000:01:00.0: enabling device (0002 -&gt; 0003)
Apr 24 11:41:47 km-MacBookPro kernel: [   15.539295] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Apr 24 11:41:47 km-MacBookPro kernel: [   15.539646] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
Apr 24 11:41:47 km-MacBookPro kernel: [   15.539655] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.76  Thu Jan 22 12:11:08 PST 2015

Apr 24 11:41:55 km-MacBookPro kernel: [   30.139286] NVRM: failed to copy vbios to system memory.
Apr 24 11:41:55 km-MacBookPro kernel: [   30.139541] NVRM: RmInitAdapter failed! (0x30:0xffffffff:747)
Apr 24 11:41:55 km-MacBookPro kernel: [   30.139546] NVRM: rm_init_adapter failed for device bearing minor number 0
Apr 24 11:41:55 km-MacBookPro kernel: [   30.139565] NVRM: nvidia_frontend_open: minor 0, module-&gt;open() failed, error -5
Apr 24 11:41:56 km-MacBookPro lightdm[855]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Apr 24 11:41:56 km-MacBookPro systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Apr 24 11:41:56 km-MacBookPro systemd[1]: Unit lightdm.service entered failed state.
Apr 24 11:41:56 km-MacBookPro systemd[1]: Triggering OnFailure= dependencies of lightdm.service.
Apr 24 11:41:56 km-MacBookPro systemd[1]: lightdm.service failed.

---

