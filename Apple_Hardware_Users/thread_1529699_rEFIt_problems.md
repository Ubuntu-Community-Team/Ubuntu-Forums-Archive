---
title: "rEFIt problems"
date: 2010-07-12
forum: Apple Hardware Users
---

### Post by nimraynn on 2010-07-12
Hi guys, wondering if I could get a bit of help here!

I'm having problems installing Ubuntu 10.04 LTS on my Apple iMac 20"...

I've installed rEFIt on the iMac, which worked perfectly fine before I started to do anything with Ubuntu. Opened up the Boot Camp Assistant, created a 40GB partition for "Windows", and booted up the Ubuntu 10.04 LTS LiveCD.

Once booted into the LiveCD, I opened up gParted. Deleted the last partition that Boot Camp created. Started up the installer & told it to use the largest unallocated space. Completed the installation & GRUB appeared to have overwritten rEFIt! :(

I tried booting OS X from GRUB, and it caused Darwin to have a kernel panic. I booted successfully into Ubuntu, but it wouldn't pick up a wireless driver...

I managed to get back into OS X by holding the option key at startup. Reinstalled rEFIt, and it started working again... sort of.

OS X boots fine using rEFIt. The Ubuntu LiveCD boots fine using rEFIt. The installed Ubuntu doesn't do anything. I get a picture of the Tux logo... but that's it. It doesn't do anything.

It was suggested in the documentation to go into rEFIt's partition tool, but I get the following error:

Status: MBR partition table is invalid, partitions overlap.

Any ideas what I can do to get Ubuntu to boot? :(

---

### Post by nimraynn on 2010-07-12
After my third attempt at following this guide: [http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

It seems to boot OK now :p

Only problem I seem to have now is using my wireless card... On the LiveCD, it asked me if I wanted to install restricted drivers, one of which was the wireless card, the other being the ATi graphics card... installed fine on the LiveCD, but it doesn't seem to prompt me for this on the complete install?

Will start googling it...

---

### Post by linuxopjemac on 2010-07-12
hook your computer up to a wired connection, then:
```
sudo apt-get update
```

Then see if you can find the hardware driver under Administration->Hardware Drivers.

you can also force to install it yourself:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by nimraynn on 2010-07-12
Thanks, unfortunately I don't have a wired connection available at the moment... I did manage to install bcmwl-kernel-source from the CD and it shows up now... but when I try to activate it, I get:

SystemError: installArchives() failed

:(

---

### Post by nimraynn on 2010-07-12
Sorted thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

;) I'm happy, for now!

---

