---
title: "Ubuntu 13.04 on MacBookPro 9,1 (Mid 2012)"
date: 2013-08-05
forum: Apple Hardware Users
---

### Post by saunite on 2013-08-05
Hi, 

Does anyone here have installed Ubuntu 13.04 on a MacBookPro 9,1 (Mid 2012)? 

I installed it this weekend and it was works really great, most things worked out of the box.

Still, I notice two issues that I wasn't able to solve yet:

1. Most of the times it doesn't boot (apparently after I installed the nvidia modules, but I am not sure), it just hangs, but if I try to boot in recovery mode and choose to continue the boot normally when prompted then it boots normally. 

I tried following this [https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-1](https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-1) and adding GRUB_PRELOAD_MODULES="efi_gap efi_vga video_bochs video_cirrus" to /etc/default/grub but apparently I don't even have those modules (trying to insmod any of those says I don't have it)

I also tried the "noefi" option on GRUB_CMDLINE_LINUX_DEFAULT on /etc/default/grub but it also didn't work (I saw that in some forum that I cannot find right now).

2. Microphone not working at all, I tried adding "options snd-hda-intel model=91" on /etc/modprobe.d/alsa-base.conf and some other variations of this line, and it also didn't work.

Does anyone have the same issues?

---

### Post by martine.ginette on 2013-10-04
Same thing here, with a MBP7.1. I'm stuck with nouveau driver and no microphone. Everything used to work fine before 13.04. Thanks for your help, anybody! Martin

---

