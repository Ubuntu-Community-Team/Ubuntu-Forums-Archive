---
title: "Can't boot into fresh install on Rev. A iMac G3"
date: 2007-10-31
forum: Apple PPC Users
---

### Post by SeveredCross on 2007-10-31
I've got a Bondi Rev. A iMac here, and figured I'd try putting Xubuntu Gutsy on it. The LiveCD boots up just fine, and the installer runs, completes without problems, but when I get to the yaboot screen, hitting Return for the first time nets the following error:

/pci@80000000/mac-io@10/ide@20000/disk@0:3,/boot/vmlinux: Input/Output Error

I have no experience with PPC/OpenFirmware, so I don't know how to rectify this. Googling has turned up nothing that could be of help, and I couldn't find anything on the forum Hitting Return again just reads "Please wait, loading kernel..." and does NOTHING.

I tried to get into OpenFirmware (trying to hold Option-Apple-O-P) to check anything there (some things on Google pointed there), but that failed.
I'm thinking about trying Edgy and hoping that it works correctly. I'd really rather not have to use Mac OS 9.2 and have the big HDD in there go to waste (160 GB).

---

### Post by SeveredCross on 2007-10-31
Just tried 6.10 alternate installer, same issue, can't boot.

Full text of what is on my screen:

Welcome to yaboot version 1.3.13
Enter "help" to get some asic usage information
boot: Linux
Please wait, loading kernel...
/pci@80000000/mac-io@10/ide@20000/disk@0:3,/boot/vmlinux: Input/Output Error
boot:
Please wait, loading kernel...

---

### Post by DRM_free on 2007-12-02
Try installing Debian or Fedora:

[http://cdimage.debian.org/debian-cd/4.0_r1/powerpc/iso-cd/debian-40r1-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r1/powerpc/iso-cd/debian-40r1-powerpc-netinst.iso)
[http://fedora.mirror.iweb.ca/releases/8/Fedora/ppc/iso/Fedora-8-ppc-rescuecd.iso](http://fedora.mirror.iweb.ca/releases/8/Fedora/ppc/iso/Fedora-8-ppc-rescuecd.iso)

If Debian and/or Fedora works and Ubuntu doesn't, please file bug in Ubuntu's Launchpad bug tracker:

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

Thanks, and please post here if you have questions.

---

### Post by hackersmovie on 2008-03-21
I've got the same exact problem here. A shame no one seems to have a solution. I may have to just stick with OS X. :(

---

### Post by adelahunty on 2008-03-21
hackersmovie - two quick questions:

1. Which machine are you using?  Is it a Rev A iMac like the original poster?

2. Have you by any chance replaced the drive with something a bit meatier?

I had the exact same problem once on a machine - sorry I can't recall which one, but I think it was a Rev A iMac.  It was expanded to an 80GB drive, and had 192MB RAM, but threw the error you mentioned.  I can't recall *exactly* what I did (was quite a while back!), but I seem to recall I needed to do a firmware update.  After that, it went swimmingly.

Whatever, I haven't had that issue since, and definitely not with newer versions of Ubuntu.

---

### Post by stream303 on 2008-03-22
> **SeveredCross said:**
> I'd really rather not have to use Mac OS 9.2 and have the big HDD in there go to waste (160 GB).

Bingo.  That model has an 8gb partition limitation unless you update the firmware from what I understand.

What you can do is use guided partitioning use up only 7.5 gb of space for safety for the whole install, and then partition the unused portion for storage or whatever.

If you are skilled at partitioning, you need to make sure to keep the boot and root partitions under 7.5 gb, and then you can go ahead and devote space to /usr /var /log etc..

For simple purposes, I think just keeping all of Ubuntu at 7.5gb and then using the rest as a general storage partition later the easier way to go.

---

