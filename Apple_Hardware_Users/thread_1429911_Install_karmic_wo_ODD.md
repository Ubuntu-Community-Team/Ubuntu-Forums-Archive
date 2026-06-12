---
title: "Install karmic w/o ODD"
date: 2010-03-14
forum: Apple Hardware Users
---

### Post by penguirl on 2010-03-14
I'd like to thank the kind souls who have the patience to answer the same noob questions over and over, you are awesome! :)

I want to install karmic only, no OS X, on my 1.25GHz G4 iMac but the ODD only reads pressed discs, not burned (I cleaned the laser to no avail). I've tried installing to it via target disk mode, the boot loader is present but I can't get past it. I followed the instructions to put the desktop installer on a flash drive but it doesn't show when I option boot (I'm still not clear if PPCs can boot from a USB device).

I presently have the iMac running karmic off of an external HDD, I just don't know how to install from this drive. Is there any way to install or copy from an external HDD to an internal HDD, or do I have to wait until I can afford a new ODD?

TIA,
Tina

---

### Post by linuxopjemac on 2010-03-15
you can just copy the whole drive onto your internal drive, be careful to know which drives zou put here:

"if" is the input interface (master) and "of" is the output interface (slave)

```
dd if=/dev/hdmaster of=/dev/hdoutput bs=512
```

exchange hdinput and hdoutput for your device (fdisk is useful to find out the names)

This will copy the whole hard disk to another hard disk, block for block. I guess that's the easiest way to do it.

[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

---

### Post by penguirl on 2010-03-17
Thank you, that worked like a charm. Unfortunately I still can't boot Ubuntu from the internal HDD, in the interim I installed OS X on it and it ran fine so I don't know what the issue is. I guess the next step is to get a DVD-RW that will read the desktop disc.

---

### Post by linuxopjemac on 2010-03-17
I guess after copying block for block the contents of your external HDD to the intermnal one, you need to adjust the /etc/yaboot.conf on the internal HDD and ybin it to make it work in the bootloader. For this to work, you need to chroot into the environment of the internal HDD. You can boot into the external HDD's Ubuntu and then chroot into the system on the internal HDD.
To chroot into a system, read [this]("http://mac.linux.be/content/chroot-system-livecd"). You need to adjust ext4 if you have another file system (Karmic Koala uses ext4, older Ubuntu versions use ext3). You also need to adjust /dev/sda4 to the internal HDD partition with Ubuntu on it.

If you are in the system, go to /etc and adjust yaboot.conf. Make sure to have linux boot on the Internal device.

More about yaboot [here]("http://mac.linux.be/content/yaboot").

After you edited yaboot.conf to your needs,
```
sudo ybin -v
```

Then reboot and hopefully you can boot into the internal HDD. You may have to use the command (alt) key at boot to achieve it.

---

### Post by penguirl on 2010-03-17
Apparently the 80GB internal drive didn't like having a 320 GB drive copied to it. I had tried to edit yaboot.conf on the boot partition of the internal drive but it was not mountable, neither was the system files partition and the swap partition was listed as a few million GBs.

I discovered that the cdrom wouldn't read the desktop dvd but it would read a burned music cd so I made a desktop cd with the 64 bit code stripped out of it and it booted just fine, I'm installed Karmic from the desktop cd to the internal hdd now and then it should just be a matter of transferring over the non-os/gui data and hopefully all will be good.

It's just as well, I had installed KDE and decided that I didn't like the KDE & GNOME mix but I wasn't very successful at uninstalling it completely. Thank you very much for your help linuxopjemac.

Addendum: for anyone unable to install from cdrom, I discovered that you have to go into open firmware to boot from a USB flash drive. [https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld]("https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld")

---

### Post by linuxopjemac on 2010-03-18
That link you provided is very useful. I will extract the most important info out of it and publish that on my website. It's very useful for people with a PPC Apple without a working CDROM drive.

---

### Post by linuxopjemac on 2010-03-18
For those of you interested in booting various media from open firmware, I wrote an updated article based on the link you gave me.

[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

accessible via [http://mac.linux.be](http://mac.linux.be) -> Apple PowerPC wiki -> Booting CD/HDD/USB/network from Open Firmware

---

### Post by penguirl on 2010-03-19
That is a very informative, well written article, I'll be sure to refer to it for my next install. I think I'll do it via USB since I've never booted from USB and I don't know anything about Open Firmware so it's an opportunity to learn. Perhaps it will be to install Lucid in the near future, how long does it take the PPC versions to be written after the x86 release?

---

### Post by linuxopjemac on 2010-03-19
I have no idea, to be honest. I am not part of that team.

---

