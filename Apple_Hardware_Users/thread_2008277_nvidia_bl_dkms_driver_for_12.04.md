---
title: "nvidia_bl_dkms driver for 12.04"
date: 2012-06-22
forum: Apple Hardware Users
---

### Post by Bergschreck on 2012-06-22
I need the nvidia_bl_dkms driver for Ubuntu 12.04. In the mactel ppa the latest version is for Natty. The apple_bl driver is loaded on my Macbook 5,1 but it is not working.
I installed the Natty version from mactel ppa, this made backlight working but gives strange error messages during boot:

```
[  195.799092] nvidia_bl: MacBook 5,1 detected
[  195.799125] nvidia_bl: Nvidia graphics adapter 10de:0863 (106b:00aa) detected
[  195.799157] ------------[ cut here ]------------
[  195.799167] WARNING: at /build/buildd/linux-3.2.0/drivers/video/backlight/backlight.c:314 backlight_device_register+0x1bd/0x200()
[  195.799171] Hardware name: MacBook5,1
[  195.799173] nvidia_backlight: invalid backlight type
[  195.799175] Modules linked in: nvidia_bl(O+) btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs reiserfs ext2 vesafb btusb snd_hda_codec_realtek nvram pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) uvcvideo videodev v4l2_compat_ioctl32 vboxdrv(O) joydev hid_apple hid_logitech_dj usbhid hid bcm5974 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm nvidia(P) snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq rfcomm parport_pc bnep applesmc input_polldev snd_timer ppdev bluetooth snd_seq_device snd lib80211_crypt_tkip binfmt_misc wl(P) soundcore snd_page_alloc shpchp lib80211 i2c_nforce2 mac_hid lp parport forcedeth
[  195.799239] Pid: 2912, comm: modprobe Tainted: P           O 3.2.0-25-generic #40-Ubuntu
[  195.799242] Call Trace:
[  195.799250]  [<ffffffff810672af>] warn_slowpath_common+0x7f/0xc0
[  195.799255]  [<ffffffff810673a6>] warn_slowpath_fmt+0x46/0x50
[  195.799260]  [<ffffffff813672b3>] ? backlight_device_register+0x1a3/0x200
[  195.799264]  [<ffffffff813672cd>] backlight_device_register+0x1bd/0x200
[  195.799271]  [<ffffffffa14b3000>] ? 0xffffffffa14b2fff
[  195.799276]  [<ffffffffa14b3351>] nvidia_bl_init+0x351/0x1000 [nvidia_bl]
[  195.799282]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[  195.799289]  [<ffffffff810a895e>] sys_init_module+0xbe/0x230
[  195.799295]  [<ffffffff81665c42>] system_call_fastpath+0x16/0x1b
[  195.799298] ---[ end trace b242b122dd6a122c ]---

```

---

