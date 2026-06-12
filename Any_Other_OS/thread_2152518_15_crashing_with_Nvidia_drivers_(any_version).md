---
title: "15 crashing with Nvidia drivers (any version)"
date: 2013-06-08
forum: Any Other OS
---

### Post by Derek10 on 2013-06-08
I have LM15 with MATE but this also happens with Cinnamon. I think this may be related to the proprietary Nvidia driver and something about HDMI. I tried many versions listed under Driver Manager and I need it so using nouveau wouldn't be a real fix here.


SOMETIMES I get a oops error on boot forcing me to reset a couple of times, eventually it'll boot and work fine. This also happened on recovery boot.

Does seem to be fine with nouveau drivers but then Chrome won't use compositing and is slower.

```
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.039409] BUG: unable to handle kernel paging request at ffff880079603fe0Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.039634] IP: [<ffffffffa0b59820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.039841] PGD 1c0e063 PUD 1fffc067 PMD 786dc063 PTE 8000000079603161
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.040168] Oops: 0003 [#1] SMP 
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.040372] Modules linked in: snd_hda_codec_hdmi coretemp snd_hda_codec_via snd_hda_intel(+) snd_hda_codec snd_hwdep(F) snd_pcm(F) kvm_intel kvm snd_page_alloc(F) nvidia(POF) gpio_ich dm_multipath(F) joydev(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) scsi_dh(F) mac_hid mei ghash_clmulni_intel(F) snd_seq_device(F) cryptd(F) serio_raw(F) lpc_ich snd_timer(F) snd(F) soundcore(F) microcode(F) btrfs(F) zlib_deflate(F) libcrc32c(F) dm_raid45 xor(F) dm_mirror(F) dm_region_hash(F) dm_log(F) hid_generic hid_logitech ff_memless usbhid hid atl1c ahci(F) libahci(F)
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.043401] CPU 0 
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.043465] Pid: 440, comm: modprobe Tainted: PF          O 3.8.0-19-generic #29-Ubuntu Gigabyte Technology Co., Ltd. H61M-S2-B3/H61M-S2-B3
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.043719] RIP: 0010:[<ffffffffa0b59820>]  [<ffffffffa0b59820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.043934] RSP: 0018:ffff880035a31ac0  EFLAGS: 00010283
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044041] RAX: 0000000000000008 RBX: 0000000000000008 RCX: ffff880075adee58
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044156] RDX: ffff880079603fd8 RSI: ffff880079603fe0 RDI: ffff880075adee40
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044270] RBP: ffff880035a31af8 R08: 0000000000000007 R09: 0000000000000006
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044384] R10: 0000000000000008 R11: 0000000000000000 R12: ffff88007ac9b800
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044499] R13: 0000000000000004 R14: 0000000000000008 R15: ffff880079604000
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044615] FS:  00007fb28e9ca740(0000) GS:ffff88007ec00000(0000) knlGS:0000000000000000
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044764] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044873] CR2: ffff880079603fe0 CR3: 000000003599c000 CR4: 00000000000407f0
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.044988] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.045102] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.045217] Process modprobe (pid: 440, threadinfo ffff880035a30000, task ffff880035dac5c0)
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.045367] Stack:
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.045460]  0000000000000006 ffffffffa0b50008 ffffffffa0b5b5d8 0000000000000001
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.045820]  ffff88007ac9b800 00000000ffffffff ffffffffa0b5d000 ffff880035a31b58
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.046180]  ffffffffa026a186 2d6164682d646e73 64692d6365646f63 313030656430313a
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.046540] Call Trace:
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.046641]  [<ffffffffa026a186>] snd_hda_codec_configure+0x146/0x440 [snd_hda_codec]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.046794]  [<ffffffffa0b792f0>] azx_probe_continue+0x3a0/0x4f0 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.046944]  [<ffffffffa0b778b0>] ? azx_attach_pcm_stream+0x1e0/0x1e0 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047095]  [<ffffffffa0b78cb0>] ? azx_halt+0x30/0x30 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047209]  [<ffffffffa0b776d0>] ? azx_pcm_trigger+0x580/0x580 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047357]  [<ffffffffa0b78810>] ? azx_runtime_suspend+0x30/0x30 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047507]  [<ffffffffa0b75670>] ? azx_pcm_free+0x50/0x50 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047623]  [<ffffffffa0b7979a>] azx_probe+0x35a/0x940 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047738]  [<ffffffff8137b47b>] local_pci_probe+0x4b/0x80
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047848]  [<ffffffff8137b7a1>] pci_device_probe+0x111/0x120
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.047959]  [<ffffffff814556c7>] driver_probe_device+0x77/0x230
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048070]  [<ffffffff8145592b>] __driver_attach+0xab/0xb0
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048180]  [<ffffffff81455880>] ? driver_probe_device+0x230/0x230
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048292]  [<ffffffff814539dd>] bus_for_each_dev+0x5d/0xa0
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048401]  [<ffffffff814551ce>] driver_attach+0x1e/0x20
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048509]  [<ffffffff81454da0>] bus_add_driver+0x190/0x280
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048619]  [<ffffffffa024f000>] ? 0xffffffffa024efff
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048726]  [<ffffffff81455ff7>] driver_register+0x77/0x170
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048835]  [<ffffffffa024f000>] ? 0xffffffffa024efff
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.048943]  [<ffffffff8137a66c>] __pci_register_driver+0x4c/0x50
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049055]  [<ffffffffa024f01e>] azx_driver_init+0x1e/0x1000 [snd_hda_intel]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049171]  [<ffffffff8100215a>] do_one_initcall+0x12a/0x180
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049284]  [<ffffffff810bfec7>] load_module+0x10c7/0x1520
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049393]  [<ffffffff810bb830>] ? unset_module_init_ro_nx+0x80/0x80
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049506]  [<ffffffff810c03e5>] sys_init_module+0xc5/0xf0
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049617]  [<ffffffff816d379d>] system_call_fastpath+0x1a/0x1f
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.049726] Code: 0f 1f 00 4d 8b bc 24 c0 00 00 00 25 00 e0 00 00 c1 e8 0c 83 c8 01 49 63 17 83 c0 01 83 f8 10 48 8d 14 92 49 8d 14 d7 48 8d 72 08 <66> 89 5a 08 c7 46 08 02 00 00 00 0f 86 5b 02 00 00 48 8d 4e 18 
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.053396] RIP  [<ffffffffa0b59820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.053600]  RSP <ffff880035a31ac0>
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.053699] CR2: ffff880079603fe0
Jun  7 11:25:27 christian-H61M-S2-B3 kernel: [    8.053799] ---[ end trace 490c03be5835d27a ]---
```

Intel celeron G530
nVIDIA geforce GT 520
Gigabte H61M-S2-B3
2GB RAM
Installed alongside Windows 8 which works fine.
Many thanks

---

### Post by buzzingrobot on 2013-06-08
There seem to be issues for some with the 13.04 kernel that ships with Mint 15.  Doing a "sudo apt-get dist-upgrade" will install a slightly newer kernel from Raring updates.  This resolved my stability issues (frequent kernel panics) when I tried Mint 15.

---

### Post by Derek10 on 2013-06-08
Once after booting I got the message

the greeter application appears to be crashing attempting to use a different one.

Clicking OK would flicker the screen and the message appear again. I don't know if related

---

### Post by Derek10 on 2013-06-08
> **buzzingrobot said:**
> There seem to be issues for some with the 13.04 kernel that ships with Mint 15.  Doing a "sudo apt-get dist-upgrade" will install a slightly newer kernel from Raring updates.  This resolved my stability issues (frequent kernel panics) when I tried Mint 15.

Thanks done that and updated the kernel. So far it's good after a couple of boots, I will report if I get another error.

---

### Post by Derek10 on 2013-06-10
I hadn't had any freeze/Kernel panic/oops error since that update so I will consider it fixed.

---

### Post by Bao2 on 2013-07-14
After I updated it was fine for some days.
Today I have same problem.

And that is why those that ranted about Unity were right: Because when forces are divided in smaller groups like Linuxmint, KDE, Unity,... bugs will stay forever. If Ubuntu were giving a normal desktop option as Interface as LinuxMint is doing, we would have less problems.

Sad days for Linux users that need CUDA in Nvidia cards. I had to go back to LinuxMint14. The 15 is just not working realibly, I had to restart today three times the 15 and you can't spent 10 minutes only to boot. So I go back to LinuxMint14.

---

### Post by Bao2 on 2013-07-15
HA! SOLVEEEEEED!!!!

You need to upgrade the kernel so Nvidia propietary drivers don't crash anymore and you can use at last CUDA without having to reboot so many times because the boot crashes.

So enter this in the terminal to upgrade and solve the problem:

sudo apt-get dist-upgrade

it upgrades the linux-headers to 3.0.28 if I remember correctly it said (the LinuxMint15 by default is 3.0.19)
SOLVED!

LOL I see it was said in post 2. But man, the rule is to mark as SOLVED a thread or people thinks the bug continues and instead reading the thread they search for a solution.
If it were marked as SOLVED I would read it to find the post with the solution! tsk, tsk...

---

### Post by sebbouckaert on 2013-08-05
Had the same issue here and 'sudo apt-get dist-upgrade' dit solve it indeed. Thanks. 
However, I have to get of my chest that these things really shouldn't t be happening anymore! I recently returned to linux after 3 years of using Windows (7). When you boot up your computer in the morning to quickly sort out a few things with very little time and the next thing you know is that the x server does not start, then all you can say is "this is really, really bad". :-(

---

### Post by buzzingrobot on 2013-08-05
No, they shouldn't happen.

My understanding, easily wrong, is that the problem with the kernel was discovered just prior to 13.04's release date. I would have voted to delay the release. More importantly, if that's what happened, it points to serious inadequacies in the testing process.  This problem, in fact, was reflected in derivative distributions that  packaged the faulty kernel despite reports of this issue. For example, Mint 15 is based on 13.04, and uses the same kernel. On the day of its release, a considerable number of kernel panic reports were posted in a very long thread at Mint's blog.

---

### Post by MattBro on 2013-08-25
I'm running linux mint 15 cinnamon,  which is based on raring I think.  The sudo apt-get dist-upgrade did nothing for me.  The cinnamon desktop freezes and I even have problems with LXDE.  X is unstable for me with my Nvidia GTX 280 card.  This is very frustrating.  Do the nuveau drivers work at all for nvidia?  It would be unfortunate to lose cuda though.

---

