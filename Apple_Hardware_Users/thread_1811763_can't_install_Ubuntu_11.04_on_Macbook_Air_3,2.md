---
title: "can't install Ubuntu 11.04 on Macbook Air 3,2"
date: 2011-07-25
forum: Apple Hardware Users
---

### Post by Harkins on 2011-07-25
The [wiki]("https://help.ubuntu.com/community/MacBookAir3-2/Narwhal") says there is a way to install [from usb]("http://ubuntuforums.org/showpost.php?p=10886829&postcount=320") but I can't get it to work on my Macbook Air 3,2 (the Nov 2010 revision, not the one from last week).

My goal is to dual-boot OS X and Ubuntu, but I can't get the Ubuntu installer to boot. I've tried a lot of variations on the instructions I've found, so I get the feeling I'm probably missing something fundamental.

I installed refit and used BootCamp to partition the drive. I downloaded desktop/alternate and i386/amd64 isos. I tried to follow the instructions to use unetbootin on OS X to install the ISOs to my USB drive, but neither drive that I connect appears in the "Drive:" selector when on OS X. I used usb-creator-gtk and unetbootin on an Unbuntu machine to try each of the four ISOs.

When I try to boot the Air from the USB drive, I got a few different types of failure:

  gpt, single fat partition, unetbootin -> alternate amd64
  result: "Non-system disk" "Press any key to reboot"

  mbr, single fat, unetbootin -> alternate amd64
  result: black screen, fan runs at 100% after a minute or two

  mbr, single fat, unetbootin -> alternate i386
  got tux with usb icon in refit
  result: "Non-system disk" "Press any key to reboot"

  mbr, single fat, unetbootin -> desktop i386
  got tux with usb icon in refit
  result: "Non-system disk" "Press any key to reboot"

  gpt, single fat partition, unetbootin -> alternate i386
  got diamond with usb icon in refit
  result: "Non-system disk" "Press any key to reboot"

  mbr, single ext4, unetbootin -> alternate i386
  got diamond with usb icon in refit
  result: "Non-system disk" "Press any key to reboot"

  mbr, single fat, unetbootin -> alternate amd64
  got colored cubes with usb and tux with usb
  cubes: got grub menu, all lead to busy cpu hang
  tux: "Non-system disk" "Press any key to reboot"

I also tried a few of these with usb-creator-gtk and got basically the same lack of results.

I tried [these instructions]("http://askubuntu.com/questions/10561/how-to-install-on-a-macbook-air-3-2-without-an-external-cd-drive") and got the same "Non-system disk" error with alternate-amd64 but didn't try all the others yet.

I tried dd'ing a disk image to my new partition as described [here]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") and [here]("http://ubuntuforums.org/showthread.php?t=1608823") with the desktop amd64 and i386 images, got a few different errors - once syslinux complaining "Error: No configuration file found" when the drive I dd'd from wasn't properly unmounted before bringing it to the Air, once I chose the drive in refit, refit displayed the single logo, and it never booted, and once I got an error I didn't copy down about needing a boot floppy.

Has anyone successfully booted Ubuntu from USB key on the Air? Exactly how did you prepare which image?

---

### Post by dobekp on 2011-07-27
Hi,

I managed to start installer using this steps:
[http://userpages.uni-koblenz.de/~ceinig/howto/artikel.php?id=92](http://userpages.uni-koblenz.de/~ceinig/howto/artikel.php?id=92)

with
Ubuntu 11.04 64bit and MB Air 3,2

but
I had no chance to enter nomodeset and the installer friezed with cursor flashing in text mode.

I will try to work it out later. I'd appreciate any hints.

---

### Post by dobekp on 2011-07-27
If I press arrow-down key during start up I can enter ubuntu instller select mode where I can change kernel options

I removed quiet and splash and set nosplash nomodeset
Start-up hanged on Performance Events (see the attachment)

---

### Post by dobekp on 2011-07-27
hurrra - it works :)

remove quiet and splash and press F6 and set acip=off nomodeset

---

### Post by Harkins on 2011-07-27
Really? Here's my console output when I try to follow along:

> ~ $ tar xzf mkisohybrid_syslinux403.tar.gz 
~ $ cd mkisohybrid/
~/mkisohybrid $ ls
bin  mkisohybrid.sh  share
~/mkisohybrid $ sudo sh mkisohybrid.sh ubuntu-11.04-desktop-amd64.iso 
Extracting ISO................................................... Done
Updating ISOLinux... Done
Rebuilding ISO....................................................... Done
Making hybrid ISO... Done
~/mkisohybrid $ ls
bin  mkisohybrid.sh  share  ubuntu-11.04-desktop-amd64_hybrid.iso
~/mkisohybrid $ sudo dd if=ubuntu-11.04-desktop-amd64_hybrid.iso of=/dev/sdb bs=1M
699+0 records in
699+0 records out
732954624 bytes (733 MB) copied, 140.31 s, 5.2 MB/s
~/mkisohybrid $ sudo eject /dev/sdb

So everything looks good there (and I checked the md5sum of the iso, and sdb really is my USB drive). In refit, I see the generic diamond icon with usb in front of it. Choosing that gets me a black screen reading only:

```
SYSLINUX 4.02 debian-20101016 EDD Copyright (C) 1994-2010 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:
```

Did you do anything else?

---

### Post by dobekp on 2011-08-10
I used Startup disc creator to copy iso image into usb.

---

### Post by Harkins on 2011-08-11
Had no luck with that either. I eventually borrowed a USB DVD drive (not a Superdrive, but it worked fine) to burn the alternate amd64 disc and boot from that to install.

---

