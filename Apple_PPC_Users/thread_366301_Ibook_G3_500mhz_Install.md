---
title: "Ibook G3 500mhz Install"
date: 2007-02-20
forum: Apple PPC Users
---

### Post by TimmyFranks on 2007-02-20
I'm trying to get Ubuntu onto my Ibook. I want it to be a dual boot so i have read all the information about using parted to resize my osx partition. I have prepared that but i'm running into a problem with my cdrom drive. It doesn't work correctly. I was wondering if anyone has had any luck with installing 6.10 over target disk mode?

---

### Post by maggot_brain on 2007-02-20
Have you checked the CD for defects before you install?  If you press the tab key at the boot prompt there should be an option there to check the CD, it will be self-evident.

Ananda

---

### Post by TimmyFranks on 2007-02-20
Yes i have checked. It is not just a problem with Ubuntu. I had to install osx over target disk mode as well. I think I am going to use Carbon Copy Cloner to backup the OSX install and do a fresh clean install of Ubuntu instead of trying to dual boot. Anyone know if Ubuntu will install over target disk mode?

---

### Post by didg on 2007-02-20
It should work  but it will fail in yaboot installer because currently yaboot bootloader is drive dependant ie. it will try to boot on /dev/sdx rather than /dev/hda. It's fixable but you need a way to boot linux on the G3 (netboot, or usb), manually fix /etc/yaboot.conf, and rerun ybin.

---

### Post by maggot_brain on 2007-02-20
Don't know if Ubuntu will install in target disk mode.  Debian will though.  You could always install Debian Sarge and upgrade to the latest Ubuntu via apt.  I will warn you though Edgy does not recognise my iBook G3 700 mhz keyboard properly and I can't fix it even though I'm an experienced Linux user.  You may be better off going with Debian anyway as Ubuntu no longer officially supports PowerPC.  You may end up in a situation where PowerPC isos are no longer available.  If you have OSX 10.4.6 or greater then you can resize HFS+ partitions from within there.  If you want to install via target disk make sure you copy the relevant files to an HFS partition not HFS+.  Once the system is booted you can alter the partitions to suit your needs.

These are the relevant sections from the manual if you decide to install Debian Etch via hard disk boot.

[http://d-i.alioth.debian.org/manual/en.powerpc/ch04s05.html#files-newworld](http://d-i.alioth.debian.org/manual/en.powerpc/ch04s05.html#files-newworld)
[http://d-i.alioth.debian.org/manual/en.powerpc/ch05s01.html#boot-newworld](http://d-i.alioth.debian.org/manual/en.powerpc/ch05s01.html#boot-newworld)

Ananda

---

### Post by TimmyFranks on 2007-02-24
Is it possible to install from an external harddrive? I have an external firewire hdd i could use. How would I go about installing the cdrom image onto the hdd for boot?

---

### Post by Gen2ly on 2007-02-24
I would do as maggot-brain suggested.  I too had isssues with Ubuntu's version of yaboot.  The boot loader is a bit out-dated and wouldn't allot me to dual-boot my iBook SE.  I just installed Debian Etch/Sarge on my iBook and it runs AWESOME.  Debian and Ubuntu are essentially the same thing so that is the way I'd go.  Here is the start page:

[Installing with the Debian Etch Installer]("http://www.debian.org/devel/debian-installer/")

---

