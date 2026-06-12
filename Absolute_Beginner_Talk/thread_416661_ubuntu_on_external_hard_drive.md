---
title: "ubuntu on external hard drive?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ramster on 2007-04-21
Hi! Previously I had trouble with partitions on a dual boot so bought an 80gb seagate hard drive for ubuntu
Changed it to ntfs and tried installing edgy eft and later dapper drake. in both cases the install froze at the installation phase. If I call up the drive it shows one folder lost+found or a repeat of the icons (examples and install). Is it possible to set up ubuntu on an external hard drive? Trying to retain windos as I cannot get thunderbird to work as mailer or firefox for internet under linux (mandriva) even though they work in windows.
ISP doesn't like linux and I'm thick as two short planks!   ramster

---

### Post by MiCovran on 2007-04-21
First of all, Firefox and Thunderbird both work in Ubuntu very well. Firefox is installed by default and you can easily install Thunderbird with Synaptic package manager. Then you simply change the "Preferred Mail Reader" to Thunderbird and that's it.

I never tried to install Ubuntu to an external hard drive, but I don't see a reason why it shouldn't work. Just be sure to select the right device for installing it to and use EXT3 partitions, not NTFS.

That's all I can help. If you still have problems, maybe someone else can help.

---

### Post by ramster on 2007-04-23
Thanks MiCovran. Got Cd burned from ISO. Seemingly loaded OK (quite a while loading the packages) and finished off with GRUB saying it would be altered but it stayed the same without any path to the external drive as promised. Called up the ex drive but had no way to get another desktop from it or even access any of the packages except bin bash init temp and so on.

---

### Post by Austin_KW on 2007-04-23
First I agree with MiCovran you dont want to be installing onto an ntfs partition. If this disk is just for ubuntu then let the installer do its magic and setup the whole disk.

Where did you install grub and which disk is your bios trying to boot from. If you had a previous installation on the first disk maybe you have now installed grub to the MBR of both disks. Try setting your bios to boot from the second disk.

---

