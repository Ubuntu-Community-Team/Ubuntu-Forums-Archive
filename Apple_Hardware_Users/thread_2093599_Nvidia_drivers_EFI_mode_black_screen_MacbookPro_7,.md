---
title: "Nvidia drivers EFI mode black screen MacbookPro 7,1 12.10"
date: 2012-12-11
forum: Apple Hardware Users
---

### Post by milan475 on 2012-12-11
Dear fellow ubuntu users,

I just installed Ubuntu 12.10 on my MacBookPro 7,1 13" (mid 2010).
I decided to run it in EFI mode since it feels more natural. 

The installation went flawlessly, WiFi wasn't working out of the box, but after installing the linux-headers and bcmwl-kernel-source, that was fixed.

The only problem I'm still experiencing now are some weird screen glitches, and random crashes that I suspect the nouveau driver of. 

The problem is that after installing the nvidia drivers by doing apt-get install nvidia-current my MacBook doesn't boot. After the ubuntu splash screen the screen just goes blank. The backlight is disabled either so it's just like my MacBook is turned of. The only thing I can do then is a reset by pressing the power button for a few seconds.

Here's what I've tried

- Installed the drivers by using the run script from nvidia.com
- Installed the latest experimental 310 version by using the bumblebee ppa
- Used nomodeset as a boot option.

The video card my macbook has is a 320M. I know my problem is probably fixed by running in BIOS emulation mode, but EFI mode just seems a lot faster. And clamshell display mode is working, which I use a lot.

Do you guys know any way to fix my problem. Or can I install a newer version of the nouveau driver that doesn't cause any screen glitches and crashes?

Thanks in advance.

---

### Post by bohm on 2013-01-06
Any luck solving this? It seems I am stuck with the exact same problem. Nouveau is freezing the screen quite often and nvidia drivers show just black screen.

---

### Post by izzo on 2013-03-04
Experiencing the same issues with nouveau freezing the system and nvidia drivers just giving a black screen (also tried bumblee, same story)on a macbook pro 6,2. Unable to find a solution thusfar, its keeping me from running ubuntu.

Anybody found a fix yet?

---

### Post by anza on 2013-03-30
I am having the same problem as well. Right now I am just not updating the drivers and my computer seems to run ok.  That being said I haven't done anything graphically intensive...

---

### Post by GhettoMrBob on 2013-04-10
Same issue here. After install I get screen artifacts and the OS freezes, all I can do is reboot back into the same deal. No issues with 12.04 once Nvidia-current installed. Even attempted upgrade to 12.10 from 12.04 and no luck that way.

On a side note, I've been testing out the 13.04 betas and so far those seem much more compatible with a wider variety of hardware. Hopefully that stays true with the true release in a few weeks.

---

### Post by martine.ginette on 2013-10-04
Same problem with 13.04. Any luck, anybody? Thanks! Martin

---

### Post by Tim_Field on 2013-10-20
If you are still having trouble booting without a black screen I found 
[http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver) 
To be helpful

However, even if I get it to boot I end up with the same issues as GhettoMrBob. I am attempting to run 13.10 on a mbp 7,1.

- Tim

---

### Post by emanuelgreisen on 2014-03-03
I am having the same issue after a fresh 12.04 reinstall. I also tried all the Nvidia driver versions I could get hold of - looking at "/var/log/syslog" after the screen has frosen (the computer actually runs just fine - but the display will stay black) I found that the Nvidia drivers somehow mess things up with a "Paging Request". It seems to be the case for all the versions I have tried with Ubuntu 12.04:

[FONT=Fixedsys]Mar  3 23:00:11 oak6 kernel: [  113.236969] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:11 oak6 kernel: [  113.237018] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:11 oak6 kernel: [  113.237047] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:11 oak6 kernel: [  113.237074] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:11 oak6 kernel: [  113.237101] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:11 oak6 kernel: [  113.237127] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:11 oak6 kernel: [  113.237153] ACPI Warning: \_SB_.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Mar  3 23:00:12 oak6 kernel: [  113.846070] BUG: unable to handle kernel paging request at 0000000000002658
Mar  3 23:00:12 oak6 kernel: [  113.846076] IP: [<ffffffffa067b7c5>] _nv007248rm+0x54/0xc4 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846206] PGD 0 
Mar  3 23:00:12 oak6 kernel: [  113.846208] Oops: 0000 [#1] SMP 
Mar  3 23:00:12 oak6 kernel: [  113.846210] Modules linked in: dm_crypt snd_hda_codec_hdmi rfcomm bnep parport_pc ppdev arc4 snd_hda_codec_cirrus brcmsmac brcmutil cordic b43 snd_hda_intel mac80211 snd_hda_codec snd_hwdep snd_pcm cfg80211 snd_seq_midi snd_rawmidi nvidia(POF) joydev ssb uvcvideo snd_seq_midi_event videobuf2_core snd_seq applesmc videodev btusb videobuf2_vmalloc input_polldev bluetooth videobuf2_memops bcm5974 snd_timer snd_seq_device intel_ips hid_appleir lpc_ich bcma snd apple_gmux soundcore snd_page_alloc apple_bl nls_iso8859_1 mac_hid lp parport hid_generic hid_apple usbhid hid i915 ahci tg3 libahci drm_kms_helper ptp firewire_ohci drm firewire_core i2c_algo_bit pps_core video crc_itu_t
Mar  3 23:00:12 oak6 kernel: [  113.846244] CPU: 1 PID: 3829 Comm: Xorg Tainted: PF          O 3.11.0-17-generic #31~precise1-Ubuntu
Mar  3 23:00:12 oak6 kernel: [  113.846246] Hardware name: Apple Inc. MacBookPro6,1/Mac-F22589C8, BIOS    MBP61.88Z.0057.B09.1004161215 04/16/10
Mar  3 23:00:12 oak6 kernel: [  113.846247] task: ffff88025ff22ee0 ti: ffff880263348000 task.ti: ffff880263348000
Mar  3 23:00:12 oak6 kernel: [  113.846249] RIP: 0010:[<ffffffffa067b7c5>]  [<ffffffffa067b7c5>] _nv007248rm+0x54/0xc4 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846350] RSP: 0018:ffff880263349988  EFLAGS: 00010282
Mar  3 23:00:12 oak6 kernel: [  113.846351] RAX: 0000000000000000 RBX: ffff88026334c008 RCX: 0000000000000000
Mar  3 23:00:12 oak6 kernel: [  113.846352] RDX: 0000000000000000 RSI: 0000000000000015 RDI: 0000000000000000
Mar  3 23:00:12 oak6 kernel: [  113.846353] RBP: ffff88025ebc5f08 R08: 0000000000000002 R09: ffff88025f6a7548
Mar  3 23:00:12 oak6 kernel: [  113.846354] R10: ffff880263395030 R11: 0000000000000000 R12: 0000000000000000
Mar  3 23:00:12 oak6 kernel: [  113.846355] R13: ffff88025fc02008 R14: 0000000000000000 R15: ffff880262ce8808
Mar  3 23:00:12 oak6 kernel: [  113.846356] FS:  00007f0e1504b880(0000) GS:ffff88026fc40000(0000) knlGS:0000000000000000
Mar  3 23:00:12 oak6 kernel: [  113.846357] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar  3 23:00:12 oak6 kernel: [  113.846358] CR2: 0000000000002658 CR3: 000000025efaa000 CR4: 00000000000007e0
Mar  3 23:00:12 oak6 kernel: [  113.846359] Stack:
Mar  3 23:00:12 oak6 kernel: [  113.846360]  ffff88025fc44008 ffff88025fc44008 0000000000000002 ffff88025fc02008
Mar  3 23:00:12 oak6 kernel: [  113.846362]  ffff88026334c008 ffffffffa06613a8 ffff8802634be008 ffff88026334c008
Mar  3 23:00:12 oak6 kernel: [  113.846364]  ffff88025fc02008 ffff88025fc02008 ffff88025eeeb008 ffffffffa06c0f5f
Mar  3 23:00:12 oak6 kernel: [  113.846366] Call Trace:
Mar  3 23:00:12 oak6 kernel: [  113.846469]  [<ffffffffa06613a8>] ? _nv007315rm+0x7f8/0x938 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846574]  [<ffffffffa06c0f5f>] ? _nv007850rm+0x80/0x276 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846683]  [<ffffffffa0739adf>] ? _nv004049rm+0x8645/0xaef1 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846790]  [<ffffffffa0738543>] ? _nv004049rm+0x70a9/0xaef1 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846829]  [<ffffffffa0366e80>] ? _nv010038rm+0x25/0x40 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846882]  [<ffffffffa0979528>] ? _nv015013rm+0x808/0x982 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846934]  [<ffffffffa097a508>] ? _nv001097rm+0x483/0x6b8 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.846986]  [<ffffffffa0972a74>] ? rm_init_adapter+0xac/0x146 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.847037]  [<ffffffffa0992e9c>] ? nv_kern_open+0x46c/0x820 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.847042]  [<ffffffff811b96a2>] ? chrdev_open+0xb2/0x1a0
Mar  3 23:00:12 oak6 kernel: [  113.847044]  [<ffffffff811b95f0>] ? cdev_put+0x30/0x30
Mar  3 23:00:12 oak6 kernel: [  113.847048]  [<ffffffff811b2076>] ? do_dentry_open+0x226/0x2a0
Mar  3 23:00:12 oak6 kernel: [  113.847050]  [<ffffffff811b2539>] ? vfs_open+0x49/0x50
Mar  3 23:00:12 oak6 kernel: [  113.847053]  [<ffffffff811c22dc>] ? do_last+0x14c/0x780
Mar  3 23:00:12 oak6 kernel: [  113.847055]  [<ffffffff811c3d34>] ? path_openat+0xc4/0x4f0
Mar  3 23:00:12 oak6 kernel: [  113.847060]  [<ffffffff81747eee>] ? _raw_spin_lock+0xe/0x20
Mar  3 23:00:12 oak6 kernel: [  113.847065]  [<ffffffff811da3b8>] ? simple_xattr_get+0x78/0xd0
Mar  3 23:00:12 oak6 kernel: [  113.847067]  [<ffffffff811c4f23>] ? do_filp_open+0x43/0xa0
Mar  3 23:00:12 oak6 kernel: [  113.847069]  [<ffffffff811d1ef5>] ? __alloc_fd+0xd5/0x160
Mar  3 23:00:12 oak6 kernel: [  113.847072]  [<ffffffff811b3be6>] ? do_sys_open+0x136/0x2a0
Mar  3 23:00:12 oak6 kernel: [  113.847074]  [<ffffffff811bedd2>] ? path_put+0x22/0x30
Mar  3 23:00:12 oak6 kernel: [  113.847075]  [<ffffffff811b3d6e>] ? SyS_open+0x1e/0x20
Mar  3 23:00:12 oak6 kernel: [  113.847080]  [<ffffffff817512dd>] ? system_call_fastpath+0x1a/0x1f
Mar  3 23:00:12 oak6 kernel: [  113.847081] Code: e0 05 00 00 00 00 00 00 41 bc 00 00 00 00 eb 18 44 89 e2 48 89 de 4c 89 ef ff 93 48 1a 00 00 01 83 e0 05 00 00 41 ff c4 4c 89 f7 <41> ff 96 58 26 00 00 44 39 e0 77 d9 ba 74 06 10 00 be 00 00 00 
Mar  3 23:00:12 oak6 kernel: [  113.847099] RIP  [<ffffffffa067b7c5>] _nv007248rm+0x54/0xc4 [nvidia]
Mar  3 23:00:12 oak6 kernel: [  113.847200]  RSP <ffff880263349988>
Mar  3 23:00:12 oak6 kernel: [  113.847201] CR2: 0000000000002658
Mar  3 23:00:12 oak6 kernel: [  113.847204] ---[ end trace b77808b442a37d16 ]---
[/FONT]

---

