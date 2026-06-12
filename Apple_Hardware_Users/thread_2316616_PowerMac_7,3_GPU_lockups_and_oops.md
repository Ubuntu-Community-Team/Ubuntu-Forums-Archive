---
title: "PowerMac 7,3: GPU lockups and oops"
date: 2016-03-09
forum: Apple Hardware Users
---

### Post by pa8600 on 2016-03-09
So I decided to install Ubuntu Mate 15.10 on my PowerMac 7,3 dual 2.0ghz, and I've been running into various issues. After I managed to install it after running into quite a few lock ups and black screens, I decided to try to find out why it was locking up. I ssh'd into the G5 from another system after X locked up logging on, and decided to try restarting lightdm. I ended up seeing garbage on the display, while dmesg gave me an oops:

> 
[  204.384014] radeon 0000:f0:10.0: ring 0 stalled for more than 143248msec
[  204.384028] radeon 0000:f0:10.0: GPU lockup (current fence id 0x000000000000024a last fence id 0x0000000000000258 on ring 0)
[  205.037776] radeon: wait for empty RBBM fifo failed ! Bad things might happen.
[  205.186695] Failed to wait GUI idle while programming pipes. Bad things might happen.
[  205.188317] Unable to handle kernel paging request for data at address 0xd000000200ca5000
[  205.188327] Faulting instruction address: 0xd000000000a3f6d0
[  205.188334] Oops: Kernel access of bad area, sig: 11 [#1]
[  205.188513] SMP NR_CPUS=1024 NUMA PowerMac
[  205.188658] Modules linked in: input_leds joydev shpchp windfarm_smu_sat mac_hid windfarm_cpufreq_clamp windfarm_pm72 windfarm_pid rtc_generic windfarm_fcu_controls windfarm_ad7417_sensor uio_pdrv_genirq uio snd_powermac snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore parport_pc ppdev lp parport autofs4 hid_generic radeon windfarm_max6690_sensor windfarm_lm75_sensor windfarm_core sungem ata_generic firewire_ohci sungem_phy firewire_core i2c_algo_bit crc_itu_t usbhid ttm hid drm_kms_helper drm uninorth_agp
[  205.190575] CPU: 1 PID: 2068 Comm: Xorg Not tainted 4.2.0-30-powerpc64-smp #36-Ubuntu
[  205.190811] task: c000000013e614b0 ti: c000000014a9c000 task.ti: c000000014a9c000
[  205.191036] NIP: d000000000a3f6d0 LR: d000000000a3f73c CTR: 0000000000004b60
[  205.191249] REGS: c000000014a9f640 TRAP: 0300   Not tainted  (4.2.0-30-powerpc64-smp)
[  205.191482] MSR: 9000000000009032 <SF,HV,EE,ME,IR,DR,RI>  CR: 84002244  XER: 00000000
[  205.191816] DAR: d000000200ca5000 DSISR: 40000000 SOFTE: 1
               GPR00: d000000000a3f73c c000000014a9f8c0 d000000000bd6870 d00000000178b000
               GPR04: d00000000179d000 c000000018117ce8 0000000294e00381 000000000000000c
               GPR08: d000000000ca5000 0000000200000000 0000000000000000 d000000000b63a30
               GPR12: 0000000044002844 c00000000fdc0900 0000000000000001 0000000000000018
               GPR16: 0000000000000000 0000000000000000 00000000210868d8 c000000014a9fb80
               GPR20: c000000014a9fa0c 0000000000000001 c00000000379c740 0000000000000000
               GPR24: c00000000379c018 0000000000000001 c000000014a9f9d0 c000000014a9f9d0
               GPR28: c00000000379d4e0 c00000000379d4b8 0000000000004b60 0000000080000001
[  205.194019] NIP [d000000000a3f6d0] .radeon_ring_backup+0x240/0x2c0 [radeon]
[  205.194264] LR [d000000000a3f73c] .radeon_ring_backup+0x2ac/0x2c0 [radeon]
[  205.194469] Call Trace:
[  205.194580] [c000000014a9f8c0] [d000000000a3f73c] .radeon_ring_backup+0x2ac/0x2c0 [radeon] (unreliable)
[  205.194914] [c000000014a9f960] [d0000000009f9de8] .radeon_gpu_reset+0x138/0x4d0 [radeon]
[  205.195208] [c000000014a9fa90] [d000000000a3c390] .radeon_gem_handle_lockup.part.0+0x20/0x50 [radeon]
[  205.195526] [c000000014a9fb10] [d0000000002d3af8] .drm_ioctl+0x288/0x5b0 [drm]
[  205.195783] [c000000014a9fc70] [d0000000009f6064] .radeon_drm_ioctl+0x64/0xc0 [radeon]
[  205.196102] [c000000014a9fd00] [d000000000b5ad5c] .radeon_kms_compat_ioctl+0x3c/0x78 [radeon]
[  205.196367] [c000000014a9fd90] [c00000000034f668] .compat_SyS_ioctl+0x128/0x380
[  205.196594] [c000000014a9fe30] [c000000000009204] system_call+0x38/0xb4
[  205.196793] Instruction dump:
[  205.196885] 39400000 39290001 7d2903a6 40be0018 48000094 60000000 60000000 60000000
[  205.197186] e87b0000 e91c0008 7be91764 3bff0001 <7d08482e> 79491764 394a0001 7d03492e
[  205.267544] ---[ end trace 77a8f4136fa83896 ]---


The GPU seems to be fine under OS X, however on Linux even if I start the system up when cold I run into various kinds of errors. Is there a fix for this, or is my GPU failing?

---

### Post by rican-linux on 2016-03-10
What radeon card do you have?

---

