---
title: "No vgaswitcheroo in /sys/kernel/debug - why not?"
date: 2012-10-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by s13_mills on 2012-10-07
Hi All,

I've been fighting with my laptop (Asus UL30VT) for the past couple of hours trying to get hybrid graphics working the way I would like - I have tried bumblebee, and found it to work well, but I am not able to use the HDMI output, which is essential for me, as my laptop is connected to my TV for a large portion of the time.

After reading around a bit, it appears the best solution for me is asus_switcheroo - but I can't get this to work! It all appears to install just fine, but I never get the /sys/kernel/debug/vgaswitcheroo/switch file, so I can never use it! I realise that this is not related to asus_switcheroo itself, but I can't seem to find what the problem is!

After trying a few different things, I did a fresh install of 12.04, then did the updates. I'm SURE I should be able to get this to work, as others with the same laptop have!

lspci |grep VGA returns:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210M] (rev a2)

```

So I definitely have two cards there - seems fine.

grep -i switcheroo /boot/config-3.2.0-* returns:
```
/boot/config-3.2.0-29-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.2.0-31-generic:CONFIG_VGA_SWITCHEROO=y

```

So the kernel should contain the vgaswitcheroo module.

I have the debugfs mounted (it is by default), as I can see other things in there, and
```
sudo mount -t debugfs none /sys/kernel/debug
```
returns:
```
mount: none already mounted or /sys/kernel/debug/ busy
mount: according to mtab, none is already mounted on /sys/kernel/debug

```

I followed the advice given in [this askubuntu question]("http://askubuntu.com/questions/57059/sys-kernel-debug-vgaswitcheroo-missing") but adding the two lines to initramfs didn't help.

I've made certain that xserver-xorg-video-nouveau and xserver-xorg-video-intel are installed.

Any more suggestions? I would really like to get this working, so I can use my laptop the way I would like to! I could just disable the Intel card with the SATA setting in the BIOS, but that slows down the drive a lot!

Thanks in advance for your help!

---

### Post by Linuxisfast on 2012-10-22
Hi have you tried Bublebee, it works well with my Intel/Nvidia graphic card laptop.

---

