---
title: "Kernel Panic when running Google Chrome"
date: 2011-09-10
forum: Any Other OS
---

### Post by markp1989 on 2011-09-10
Just installed Debian stable on my desktop and laptop.

both of them are having kernel panics when google chrome is running. 


here is dmesg on my laptop from around the time of the error 
```
[32639.468123] Modules linked in: parport_pc ppdev lp parport sco bridge stp rfcomm bnep l2cap bluetooth cpufreq_stats cpufreq_conservative cpufreq_powersave cpufreq_userspace binfmt_misc uinput fuse ext3 jbd loop snd_hda_codec_intelhdmi snd_hda_codec_realtek joydev arc4 ecb snd_hda_intel snd_hda_codec snd_hwdep ath9k uvcvideo i915 snd_pcm mac80211 videodev drm_kms_helper snd_seq ath v4l1_compat drm snd_timer snd_seq_device v4l2_compat_ioctl32 cfg80211 psmouse i2c_algo_bit snd pcspkr evdev serio_raw asus_laptop rfkill i2c_core soundcore led_class snd_page_alloc battery video ac output button processor ext4 mbcache jbd2 crc16 sha256_generic aes_x86_64 aes_generic cbc dm_crypt dm_mod sd_mod crc_t10dif ahci libata uhci_hcd thermal atl1c ehci_hcd scsi_mod thermal_sys usbcore nls_base [last unloaded: scsi_wait_scan]
[32639.468224] Pid: 5938, comm: chrome Tainted: G      D    2.6.32-5-amd64 #1 UL30A               
[32639.468228] RIP: 0010:[<ffffffff8112f98d>]  [<ffffffff8112f98d>] m_stop+0x15/0x4c
[32639.468236] RSP: 0018:ffff88013da13e88  EFLAGS: 00010286
[32639.468240] RAX: ffffffff8131fab0 RBX: ffff88013da13ed8 RCX: 000000d0d6df6000
[32639.468244] RDX: 00000000ffffff00 RSI: fffffffffffffff3 RDI: ffff88013da3c280
[32639.468248] RBP: ffff88013da2caa0 R08: ffff88013c65df80 R09: 0000000000000002
[32639.468253] R10: 0000000000000022 R11: ffffffff811516f3 R12: fffffffffffffff3
[32639.468257] R13: 00000000fffffff3 R14: 0000000000000000 R15: 0000000000010000
[32639.468262] FS:  00007fc8e955a7e0(0000) GS:ffff880005200000(0000) knlGS:0000000000000000
[32639.468266] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[32639.468270] CR2: fffffffffffffff3 CR3: 0000000125bb7000 CR4: 00000000000406f0
[32639.468274] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[32639.468279] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[32639.468284] Process chrome (pid: 5938, threadinfo ffff88013da12000, task ffff88013c503170)
[32639.468287] Stack:
[32639.468289]  0000000000001000 ffff88013da13ed8 ffff88013da3c280 ffffffff81105aa9
[32639.468295] <0> 0000000000001000 ffff88013da13f50 00007fff7f97a1f0 ffff880125b27240
[32639.468302] <0> ffff88013da3c2b8 0000000000000001 0000000000000000 0000000000010000
[32639.468310] Call Trace:
[32639.468317]  [<ffffffff81105aa9>] ? seq_read+0x269/0x388
[32639.468324]  [<ffffffff810ef510>] ? vfs_read+0xa6/0xff
[32639.468329]  [<ffffffff810ef625>] ? sys_read+0x45/0x6e
[32639.468336]  [<ffffffff81010b42>] ? system_call_fastpath+0x16/0x1b
[32639.468340] Code: 48 89 df e8 e3 c2 f1 ff 31 c0 40 84 ed 49 0f 45 c4 5b 5d 41 5c c3 55 53 48 83 ec 08 48 85 f6 48 8b 6f 60 74 1a 48 3b 75 10 74 14 <48> 8b 1e 48 8d 7b 60 e8 dd 86 f3 ff 48 89 df e8 ac c2 f1 ff 48 
[32639.468390] RIP  [<ffffffff8112f98d>] m_stop+0x15/0x4c
[32639.468397]  RSP <ffff88013da13e88>
[32639.468399] CR2: fffffffffffffff3
[32639.468404] ---[ end trace 4159702131caeb39 ]---
mark@mark-laptop:~$ 

```

has anyone else had this problem?

I did try installing chromium instead of chrome, but there are some addons I need, that I cannot install through the chrome addon website as it says i need the newest version of chrome. 

Thanks in advanced for any help.

---

### Post by humla on 2011-09-11
yes, and its likely because of the recent upgrade of the kernel to 2.6.32-5. Is this the kernel version u have?

If so just upgrade the kernel manually and it should be ok or u could just wait for a debian update of kernel which i hope is coming soon.

EDIT: and just as i say it, the updates are available, its the same version though, but i think they have patched it.

---

### Post by drawkcab on 2011-09-12
Both chrome and chromium have been working fine in Linux Mint Debian Edition.  I wonder what the relevant difference is.

---

### Post by amjjawad on 2011-09-14
Never had such a problem!

---

### Post by markp1989 on 2011-09-15
> **humla said:**
> yes, and its likely because of the recent upgrade of the kernel to 2.6.32-5. Is this the kernel version u have?

If so just upgrade the kernel manually and it should be ok or u could just wait for a debian update of kernel which i hope is coming soon.

EDIT: and just as i say it, the updates are available, its the same version though, but i think they have patched it.

Thanks for replying.

I just installed the kernel update, I had version 2.6.32-5, like you said there was an update with the same version number.

I have installed the update and I am running chrome right now on my desktop, no problems so far *fingers crossed*

Assuming it is ok for tonight I will install the update on my laptop to check it.

I will reply depending on the outcome :)

---

### Post by markp1989 on 2011-09-17
update seems to have solved it on both of the machines :) 

Thread marked as solved.

Thankyou :)

---

