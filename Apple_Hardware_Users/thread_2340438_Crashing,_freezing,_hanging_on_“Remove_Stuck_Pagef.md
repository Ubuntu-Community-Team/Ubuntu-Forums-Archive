---
title: "Crashing, freezing, hanging on “Remove Stuck Pageflip”"
date: 2016-10-18
forum: Apple Hardware Users
---

### Post by komali2 on 2016-10-18
I've been having trouble with this Ubuntu installation on my Macbook Pro A5102 for the last few days. Hangs, crashes, freezes, the works. I've managed to grab a logfile from a relatively short timeframe that had a truly shocking number of crashes and hangs - 5 in 5 minutes. I'm strolling through it but don't really know what I'm looking at / for. If anybody could help me read this thing and debug this issue, I'd be tremendously grateful.

System:

```
Macbook Pro A1502 13in Retina
``````

OS: Ubuntu 16.04 LTS
Memory: 7.7 GiB
Processor: Intel® Core&#8482; i5-5257U CPU @ 2.70GHz × 4 
Graphics: Intel® Iris 6100 (Broadwell GT3) 
OS type: 64-bit
Disk: 37.0 GB
```

State:


[LIST]
[*=1]Laptop plugged in to power.
[*=1]USB dongle plugged in top-right port, connected to mouse/keyboard combo
[*=1]External monitor plugged in via displayport
[*=1]Headphones plugged in 3.5mm audio jack.
[*=1]Wifi connected
[/LIST]

Issue:

Machine will at random crash, hang, or freeze. Syslog will report variation on "kicking stuck page flip" or "removing stuck page flip." 

EDIT: A bug report has been issued here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1636327](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1636327)
And there's been discussion at this open Stackoverflow question with a bounty on it: [http://askubuntu.com/questions/838855/crashing-freezing-hanging-on-remove-stuck-pageflip](http://askubuntu.com/questions/838855/crashing-freezing-hanging-on-remove-stuck-pageflip)

EDIT: This bug is pervasive and not restricted to apple hardware. It is being reported by fedora, arch, gentoo users: 

[https://bugzilla.redhat.com/show_bug.cgi?id=1195870](https://bugzilla.redhat.com/show_bug.cgi?id=1195870)


[https://bbs.archlinux.org/viewtopic.php?id=195844](https://bbs.archlinux.org/viewtopic.php?id=195844)

[https://forums.gentoo.org/viewtopic-t-1007522-start-0-postdays-0-postorder-asc-highlight-.html?sid=d3eb60fa12c717debf91cf0550e2d7ee](https://forums.gentoo.org/viewtopic-t-1007522-start-0-postdays-0-postorder-asc-highlight-.html?sid=d3eb60fa12c717debf91cf0550e2d7ee)

---

### Post by QIII on 2016-10-18
Moved to **Apple Hardware Users** for more likely help.

---

### Post by komali2 on 2016-10-19
Finally caught a log from a crash

```

Oct 19 10:31:37 caleb-ubuntu kernel: [ 2424.426761] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.426594] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430445] ------------[ cut here ]------------
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430544] WARNING: CPU: 3 PID: 1064 at /build/linux-e0bh4_/linux-4.4.0/drivers/gpu/drm/i915/intel_display.c:11408 intel_check_page_flip+0xfb/0x110 [i915]()
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430549] Kicking stuck page flip: queued at 115866, now 115867
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430551] Modules linked in: nvram rfcomm msr bnep snd_hda_codec_hdmi btusb btrtl btbcm btintel bluetooth joydev input_leds bcm5974 binfmt_misc nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass snd_hda_codec_cirrus snd_hda_codec_generic snd_hda_intel crct10dif_pclmul snd_hda_codec crc32_pclmul snd_hda_core snd_hwdep aesni_intel snd_pcm applesmc input_polldev aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi brcmfmac snd_seq intel_pch_thermal brcmutil snd_seq_device snd_timer lpc_ich cfg80211 thunderbolt snd bdc_pci mei_me shpchp mei soundcore sbs acpi_als sbshc kfifo_buf industrialio apple_bl spi_pxa2xx_platform mac_hid parport_pc ppdev lp parport autofs4 hid_apple hid_generic i915 i2c_algo_bit drm_kms_helper usbhid syscopyarea hid sysfillrect ahci sysimgblt fb_sys_fops libahci drm uas usb_storage fjes video
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430664] CPU: 3 PID: 1064 Comm: Xorg Not tainted 4.4.0-42-generic #62-Ubuntu
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430667] Hardware name: Apple Inc. MacBookPro12,1/Mac-E43C1C25D4880AD6, BIOS MBP121.88Z.0167.B16.1602111810 02/11/2016
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430671]  0000000000000086 000000007a2cda97 ffff88026ecc3d88 ffffffff813f1f83
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430676]  ffff88026ecc3dd0 ffffffffc0258ab8 ffff88026ecc3dc0 ffffffff81081212
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430681]  ffff88025f58d800 ffff880035d42000 ffff88025f58d9a8 0000000000000000
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430686] Call Trace:
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430690]  <IRQ>  [<ffffffff813f1f83>] dump_stack+0x63/0x90
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430710]  [<ffffffff81081212>] warn_slowpath_common+0x82/0xc0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430717]  [<ffffffff810812ac>] warn_slowpath_fmt+0x5c/0x80
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430786]  [<ffffffffc01fbbdb>] intel_check_page_flip+0xfb/0x110 [i915]
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430845]  [<ffffffffc018215f>] gen8_irq_handler+0x34f/0x740 [i915]
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430857]  [<ffffffff810daced>] handle_irq_event_percpu+0x8d/0x1d0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430861]  [<ffffffff810dae6e>] handle_irq_event+0x3e/0x60
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430866]  [<ffffffff810de3ad>] handle_edge_irq+0x7d/0x150
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430876]  [<ffffffff810310fa>] handle_irq+0x1a/0x30
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430883]  [<ffffffff8183429b>] do_IRQ+0x4b/0xd0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430889]  [<ffffffff81832382>] common_interrupt+0x82/0x82
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430891]  <EOI>  [<ffffffff817cb0ec>] ? unix_poll+0x2c/0xc0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430909]  [<ffffffff81709a97>] sock_poll+0x107/0x120
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430921]  [<ffffffff812224d3>] do_select+0x383/0x810
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430929]  [<ffffffff811efc19>] ? __kmalloc_node_track_caller+0x249/0x310
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430935]  [<ffffffff81221bc0>] ? poll_initwait+0x50/0x50
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430940]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430943]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430948]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430953]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430956]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430959]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430964]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430968]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430971]  [<ffffffff81221f20>] ? poll_select_copy_remaining+0x140/0x140
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430974]  [<ffffffff81222b2f>] core_sys_select+0x1cf/0x2f0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430983]  [<ffffffff8120db66>] ? do_readv_writev+0x146/0x230
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430992]  [<ffffffff813fae09>] ? timerqueue_add+0x59/0xb0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.430998]  [<ffffffff813faea4>] ? timerqueue_del+0x24/0x70
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431004]  [<ffffffff810ef2fc>] ? __remove_hrtimer+0x3c/0x90
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431008]  [<ffffffff810ef421>] ? hrtimer_try_to_cancel+0xd1/0x130
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431015]  [<ffffffff810f4c4a>] ? ktime_get_ts64+0x4a/0xf0
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431021]  [<ffffffff81222d0a>] SyS_select+0xba/0x110
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431030]  [<ffffffff818318b2>] entry_SYSCALL_64_fastpath+0x16/0x71
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431034]  [<ffffffff81831883>] ? entry_SYSCALL_64_after_swapgs+0x30/0x49
Oct 19 10:31:39 caleb-ubuntu kernel: [ 2426.431038] ---[ end trace e5e8068a0c995716 ]---



```

This is caused by the "Removing stuck page flip" bug that is apparently as ancient as 2012. I have found a lot of reports on it, but never any solutions other than "this was fixed in Ubuntu 14.. 15..." etc, followed instantly by users reporting "nope, no it wasn't." 

If anybody has more information on this I'd be grateful. 

I have updated to the latest Intel video drivers. 

More bug reports making suspect it is "removing stuck page flip" :

```


Oct 19 14:24:51 caleb-ubuntu kernel: [ 1188.849673] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.449814] ------------[ cut here ]------------
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.449910] WARNING: CPU: 1 PID: 973 at /var/lib/dkms/i915-4.6.3-4.4.0/1/build/drivers/gpu/drm/i915/intel_display.c:3931 intel_atomic_commit+0x15c4/0x1640 [i915]()
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.449914] Removing stuck page flip
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.449917] Modules linked in: snd_seq_dummy nvram rfcomm bnep btusb btrtl btbcm btintel input_leds joydev bcm5974 bluetooth msr binfmt_misc snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul nls_iso8859_1 aesni_intel brcmfmac aes_x86_64 applesmc lrw input_polldev gf128mul glue_helper ablk_helper cryptd snd_hda_codec_cirrus snd_hda_codec_generic brcmutil cfg80211 snd_seq_midi snd_hda_intel snd_seq_midi_event intel_pch_thermal snd_hda_codec snd_hda_core snd_rawmidi snd_hwdep lpc_ich snd_seq thunderbolt mei_me bdc_pci snd_pcm mei snd_seq_device shpchp snd_timer snd soundcore sbs acpi_als sbshc kfifo_buf industrialio mac_hid spi_pxa2xx_platform apple_bl parport_pc ppdev lp parport autofs4 hid_apple hid_generic usbhid hid i915(OE) i2c_algo_bit drm_kms_helper(OE) syscopyarea sysfillrect sysimgblt ahci fb_sys_fops libahci drm video fjes uas usb_storage
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450030] CPU: 1 PID: 973 Comm: Xorg Tainted: G           OE   4.4.0-43-generic #63-Ubuntu
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450034] Hardware name: Apple Inc. MacBookPro12,1/Mac-E43C1C25D4880AD6, BIOS MBP121.88Z.0167.B16.1602111810 02/11/2016
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450038]  0000000000000086 00000000bb9a1ca9 ffff880070623af8 ffffffff813f1f93
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450044]  ffff880070623b40 ffffffffc02150d0 ffff880070623b30 ffffffff81081212
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450050]  0000000000000000 ffff880264fcb9a8 0000000000000000 ffff88025fa9f000
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450056] Call Trace:
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450068]  [<ffffffff813f1f93>] dump_stack+0x63/0x90
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450077]  [<ffffffff81081212>] warn_slowpath_common+0x82/0xc0
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450082]  [<ffffffff810812ac>] warn_slowpath_fmt+0x5c/0x80
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450091]  [<ffffffff810c3935>] ? finish_wait+0x55/0x70
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450152]  [<ffffffffc019f714>] intel_atomic_commit+0x15c4/0x1640 [i915]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450160]  [<ffffffff810c3dd0>] ? wake_atomic_t_function+0x60/0x60
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450215]  [<ffffffffc006fbde>] ? drm_atomic_check_only+0x18e/0x590 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450255]  [<ffffffffc0070017>] drm_atomic_commit+0x37/0x60 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450284]  [<ffffffffc00fb8c9>] drm_atomic_helper_disable_plane+0xa9/0xf0 [drm_kms_helper]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450317]  [<ffffffffc005f269>] __setplane_internal+0x169/0x250 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450356]  [<ffffffffc006e79a>] ? drm_modeset_lock_all_ctx+0x9a/0xb0 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450392]  [<ffffffffc0063056>] drm_mode_setplane+0x136/0x1b0 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450419]  [<ffffffffc0054752>] drm_ioctl+0x152/0x540 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450453]  [<ffffffffc0062f20>] ? drm_plane_check_pixel_format+0x50/0x50 [drm]
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450463]  [<ffffffff8122123f>] do_vfs_ioctl+0x29f/0x490
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450469]  [<ffffffff8120fde1>] ? __sb_end_write+0x21/0x30
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450476]  [<ffffffff8120d9ed>] ? vfs_write+0x15d/0x1a0
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450481]  [<ffffffff812214a9>] SyS_ioctl+0x79/0x90
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450489]  [<ffffffff818318b2>] entry_SYSCALL_64_fastpath+0x16/0x71
Oct 19 14:24:51 caleb-ubuntu kernel: [ 1189.450493] ---[ end trace 633a0aa7b384f0dd ]---

```

```

Oct 19 11:22:45 caleb-ubuntu kernel: [ 2370.589690] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 19 11:22:47 caleb-ubuntu kernel: [ 2372.589489] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653528] ------------[ cut here ]------------
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653555] WARNING: CPU: 2 PID: 1033 at /build/linux-e0bh4_/linux-4.4.0/drivers/gpu/drm/i915/intel_display.c:3963 intel_crtc_wait_for_pending_flips+0x1e2/0x240 [i915]()
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653556] WARN_ON(wait_event_timeout(dev_priv->pending_flip_queue, !intel_crtc_has_pending_flip(crtc), 60*HZ) == 0)
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653557] Modules linked in: snd_seq_dummy btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c cpuid rfcomm nvram bnep btusb btrtl btbcm joydev btintel input_leds bcm5974 bluetooth msr binfmt_misc nls_iso8859_1 applesmc intel_rapl x86_pkg_temp_thermal input_polldev intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul brcmfmac brcmutil snd_hda_codec_cirrus cfg80211 snd_hda_codec_generic aesni_intel aes_x86_64 lrw snd_hda_codec_hdmi gf128mul glue_helper ablk_helper cryptd bdc_pci thunderbolt snd_hda_intel snd_hda_codec lpc_ich intel_pch_thermal shpchp mei_me snd_hda_core mei snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi acpi_als kfifo_buf snd_seq sbs industrialio sbshc snd_seq_device snd_timer spi_pxa2xx_platform apple_bl snd soundcore mac_hid parport_pc ppdev lp parport autofs4 hid_apple hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper syscopyarea ahci sysfillrect uas libahci sysimgblt fb_sys_fops usb_storage drm fjes video
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653597] CPU: 2 PID: 1033 Comm: Xorg Tainted: G        W       4.4.0-42-generic #62-Ubuntu
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653598] Hardware name: Apple Inc. MacBookPro12,1/Mac-E43C1C25D4880AD6, BIOS MBP121.88Z.0167.B16.1602111810 02/11/2016
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653599]  0000000000000286 000000004413e07b ffff88003533faa0 ffffffff813f1f83
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653601]  ffff88003533fae8 ffffffffc020eab8 ffff88003533fad8 ffffffff81081212
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653602]  ffff880264f629a8 ffff8800357b9030 ffff880264822000 ffff880264f62800
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653604] Call Trace:
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653608]  [<ffffffff813f1f83>] dump_stack+0x63/0x90
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653610]  [<ffffffff81081212>] warn_slowpath_common+0x82/0xc0
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653612]  [<ffffffff810812ac>] warn_slowpath_fmt+0x5c/0x80
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653614]  [<ffffffff810c3935>] ? finish_wait+0x55/0x70
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653630]  [<ffffffffc01a92a2>] intel_crtc_wait_for_pending_flips+0x1e2/0x240 [i915]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653632]  [<ffffffff810c3dd0>] ? wake_atomic_t_function+0x60/0x60
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653648]  [<ffffffffc01aa521>] intel_pre_plane_update+0x111/0x140 [i915]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653664]  [<ffffffffc01aacf2>] intel_atomic_commit+0x352/0x6f0 [i915]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653678]  [<ffffffffc003cbde>] ? drm_atomic_check_only+0x18e/0x590 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653689]  [<ffffffffc003d017>] drm_atomic_commit+0x37/0x60 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653696]  [<ffffffffc0104939>] drm_atomic_helper_disable_plane+0xa9/0xf0 [drm_kms_helper]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653704]  [<ffffffffc002c269>] __setplane_internal+0x169/0x250 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653714]  [<ffffffffc003b79a>] ? drm_modeset_lock_all_ctx+0x9a/0xb0 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653723]  [<ffffffffc0030056>] drm_mode_setplane+0x136/0x1b0 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653730]  [<ffffffffc0021752>] drm_ioctl+0x152/0x540 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653739]  [<ffffffffc002ff20>] ? drm_plane_check_pixel_format+0x50/0x50 [drm]
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653742]  [<ffffffff8122122f>] do_vfs_ioctl+0x29f/0x490
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653743]  [<ffffffff8120fdd1>] ? __sb_end_write+0x21/0x30
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653746]  [<ffffffff8120d9dd>] ? vfs_write+0x15d/0x1a0
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653747]  [<ffffffff81221499>] SyS_ioctl+0x79/0x90
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653750]  [<ffffffff818318b2>] entry_SYSCALL_64_fastpath+0x16/0x71
Oct 19 11:22:48 caleb-ubuntu kernel: [ 2373.653751] ---[ end trace c2690206b3e3a013 ]---
Oct 19 11:22:49 caleb-ubuntu kernel: [ 2374.589344] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 19 11:22:51 caleb-ubuntu kernel: [ 2376.589288] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes


```

Just happened three times in a row

```

Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454419] ------------[ cut here ]------------
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454447] WARNING: CPU: 2 PID: 1070 at /var/lib/dkms/i915-4.6.3-4.4.0/1/build/drivers/gpu/drm/i915/intel_display.c:3931 intel_atomic_commit+0x15c4/0x1640 [i915]()
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454448] Removing stuck page flip
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454449] Modules linked in: snd_seq_dummy nvram rfcomm msr bnep btusb btrtl btbcm btintel bluetooth input_leds joydev bcm5974 snd_hda_codec_hdmi binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass nls_iso8859_1 crct10dif_pclmul crc32_pclmul snd_hda_codec_cirrus applesmc snd_hda_codec_generic input_polldev aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm lpc_ich snd_seq_midi intel_pch_thermal snd_seq_midi_event brcmfmac snd_rawmidi brcmutil cfg80211 snd_seq thunderbolt snd_seq_device bdc_pci snd_timer mei_me snd shpchp mei soundcore sbs sbshc acpi_als kfifo_buf apple_bl industrialio spi_pxa2xx_platform mac_hid parport_pc ppdev lp parport autofs4 hid_apple hid_generic usbhid hid uas i915(OE) i2c_algo_bit drm_kms_helper(OE) syscopyarea sysfillrect sysimgblt fb_sys_fops ahci drm libahci usb_storage fjes video
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454485] CPU: 2 PID: 1070 Comm: Xorg Tainted: G        W  OE   4.4.0-43-generic #63-Ubuntu
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454486] Hardware name: Apple Inc. MacBookPro12,1/Mac-E43C1C25D4880AD6, BIOS MBP121.88Z.0167.B16.1602111810 02/11/2016
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454487]  0000000000000086 0000000041bba34a ffff8802613bfaf8 ffffffff813f1f93
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454489]  ffff8802613bfb40 ffffffffc02130d0 ffff8802613bfb30 ffffffff81081212
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454490]  0000000000000000 ffff8800355631a8 0000000000000000 ffff8800357e8000
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454492] Call Trace:
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454496]  [<ffffffff813f1f93>] dump_stack+0x63/0x90
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454498]  [<ffffffff81081212>] warn_slowpath_common+0x82/0xc0
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454500]  [<ffffffff810812ac>] warn_slowpath_fmt+0x5c/0x80
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454502]  [<ffffffff810c3935>] ? finish_wait+0x55/0x70
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454517]  [<ffffffffc019d714>] intel_atomic_commit+0x15c4/0x1640 [i915]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454519]  [<ffffffff810c3dd0>] ? wake_atomic_t_function+0x60/0x60
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454533]  [<ffffffffc0058bde>] ? drm_atomic_check_only+0x18e/0x590 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454541]  [<ffffffffc0059017>] drm_atomic_commit+0x37/0x60 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454549]  [<ffffffffc00f98c9>] drm_atomic_helper_disable_plane+0xa9/0xf0 [drm_kms_helper]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454557]  [<ffffffffc0048269>] __setplane_internal+0x169/0x250 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454566]  [<ffffffffc005779a>] ? drm_modeset_lock_all_ctx+0x9a/0xb0 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454575]  [<ffffffffc004c056>] drm_mode_setplane+0x136/0x1b0 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454581]  [<ffffffffc003d752>] drm_ioctl+0x152/0x540 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454588]  [<ffffffffc004bf20>] ? drm_plane_check_pixel_format+0x50/0x50 [drm]
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454592]  [<ffffffff8122123f>] do_vfs_ioctl+0x29f/0x490
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454593]  [<ffffffff8120fde1>] ? __sb_end_write+0x21/0x30
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454595]  [<ffffffff8120d9ed>] ? vfs_write+0x15d/0x1a0
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454596]  [<ffffffff812214a9>] SyS_ioctl+0x79/0x90
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454599]  [<ffffffff818318b2>] entry_SYSCALL_64_fastpath+0x16/0x71
Oct 20 10:52:33 caleb-ubuntu kernel: [ 3691.454600] ---[ end trace 3f5153c0fc8dac98 ]---
Oct 20 10:52:35 caleb-ubuntu kernel: [ 3693.434431] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
Oct 20 10:52:37 caleb-ubuntu kernel: [ 3695.438302] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes

```

```

Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620121] ------------[ cut here ]------------
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620165] WARNING: CPU: 3 PID: 0 at /var/lib/dkms/i915-4.6.3-4.4.0/1/build/drivers/gpu/drm/i915/intel_display.c:11488 intel_check_page_flip+0xfb/0x110 [i915]()
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620167] Kicking stuck page flip: queued at 184191, now 184192
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620169] Modules linked in: snd_seq_dummy nvram rfcomm msr bnep btusb btrtl btbcm btintel bluetooth input_leds joydev bcm5974 snd_hda_codec_hdmi binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass nls_iso8859_1 crct10dif_pclmul crc32_pclmul snd_hda_codec_cirrus applesmc snd_hda_codec_generic input_polldev aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm lpc_ich snd_seq_midi intel_pch_thermal snd_seq_midi_event brcmfmac snd_rawmidi brcmutil cfg80211 snd_seq thunderbolt snd_seq_device bdc_pci snd_timer mei_me snd shpchp mei soundcore sbs sbshc acpi_als kfifo_buf apple_bl industrialio spi_pxa2xx_platform mac_hid parport_pc ppdev lp parport autofs4 hid_apple hid_generic usbhid hid uas i915(OE) i2c_algo_bit drm_kms_helper(OE) syscopyarea sysfillrect sysimgblt fb_sys_fops ahci drm libahci usb_storage fjes video
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620225] CPU: 3 PID: 0 Comm: swapper/3 Tainted: G           OE   4.4.0-43-generic #63-Ubuntu
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620226] Hardware name: Apple Inc. MacBookPro12,1/Mac-E43C1C25D4880AD6, BIOS MBP121.88Z.0167.B16.1602111810 02/11/2016
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620228]  0000000000000086 68d9ba824d00b154 ffff88026ecc3d80 ffffffff813f1f93
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620231]  ffff88026ecc3dc8 ffffffffc02130d0 ffff88026ecc3db8 ffffffff81081212
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620234]  ffff880035563000 ffff8800357e8000 ffff8800355631a8 0000000000000000
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620236] Call Trace:
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620238]  <IRQ>  [<ffffffff813f1f93>] dump_stack+0x63/0x90
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620247]  [<ffffffff81081212>] warn_slowpath_common+0x82/0xc0
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620249]  [<ffffffff810812ac>] warn_slowpath_fmt+0x5c/0x80
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620274]  [<ffffffffc01a42eb>] intel_check_page_flip+0xfb/0x110 [i915]
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620293]  [<ffffffffc01321bb>] gen8_irq_handler+0x31b/0x6b0 [i915]
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620296]  [<ffffffff810daced>] handle_irq_event_percpu+0x8d/0x1d0
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620298]  [<ffffffff810dae6e>] handle_irq_event+0x3e/0x60
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620301]  [<ffffffff810de3ad>] handle_edge_irq+0x7d/0x150
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620304]  [<ffffffff810310fa>] handle_irq+0x1a/0x30
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620308]  [<ffffffff8183429b>] do_IRQ+0x4b/0xd0
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620311]  [<ffffffff81832382>] common_interrupt+0x82/0x82
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620312]  <EOI>  [<ffffffff816c4d81>] ? cpuidle_enter_state+0x111/0x2b0
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620318]  [<ffffffff816c4f57>] cpuidle_enter+0x17/0x20
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620322]  [<ffffffff810c4112>] call_cpuidle+0x32/0x60
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620325]  [<ffffffff816c4f33>] ? cpuidle_select+0x13/0x20
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620327]  [<ffffffff810c43d0>] cpu_startup_entry+0x290/0x350
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620330]  [<ffffffff810516e4>] start_secondary+0x154/0x190
Oct 20 10:50:30 caleb-ubuntu kernel: [ 3568.620332] ---[ end trace 3f5153c0fc8dac97 ]---
Oct 20 10:50:32 caleb-ubuntu kernel: [ 3570.603157] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes


```

I put a question on the ubuntu stack overflow with 50 bounty if you want it: 

[http://askubuntu.com/questions/838855/crashing-freezing-hanging-on-remove-stuck-pageflip](http://askubuntu.com/questions/838855/crashing-freezing-hanging-on-remove-stuck-pageflip)

---

