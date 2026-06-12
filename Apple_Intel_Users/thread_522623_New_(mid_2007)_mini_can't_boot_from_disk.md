---
title: "New (mid 2007) mini can't boot from disk"
date: 2007-08-10
forum: Apple Intel Users
---

### Post by demyers on 2007-08-10
I'm trying to install Feisty on a new Mac mini (mid 2007 refresh).  I'd like to have only Ubuntu on this box, so I'd like to wipe out Mac OS and not use Boot Camp.

The Live CD works fine and installation proceeds without errors.  However the system won't boot from the hard disk after installation.  After the white screen appears for a few seconds, video shuts off and the system just sits there.  It's like GRUB never gets called.

When I look at the disk from the Live CD it looks OK.  It looks like an MBR disk with one primary partition marked for boot and an extended partition for swap.  I've tried reinstalling GRUB a few times.

There are a lot of articles out there about installing Ubuntu on Macs, but no two of them say the same thing.  It's really quite confusing.

Anyone else tried a new mini yet?  Perhaps there's a firmware change in the new systems that's causing things to break.

I have not yet tried rEFIt, Gutsy, or 64-bit Feisty.  I might have to end up reinstalling Mac OS and using rEFIt and Boot Camp, though I'd rather not.

Thanks for any advice.

---

### Post by cyberdork33 on 2007-08-11
new computer, new problems...

My guess is the firmware has changed.

---

### Post by benanzo on 2007-08-11
It sounds like there's no BIOS emulation built into the EFI firmware.  Apple's implementation of Intel's EFI specification is (so far) very limited.  With the 10.4.6 OS X update there was an EFI firmware update that added BIOS/MBR support.

I would try installing OS X and running all the updates.  Then try installing Ubuntu.  Perhaps the machine wasn't updated.

Good Luck!

---

### Post by pxwpxw on 2007-08-11
You could download the refit bootable CD iso,  to run gptsync. That might fix it without the full macosx reinstall.

 [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Explanation here:

 [http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)
> 
Fact: You need a MBR partition table to use LILO/GRUB
====
And -
The Boot Camp Assistant (and diskutil) already creates a hybrid GPT/MBR partition table. There is no need to clean up after them, and gptsync will just tell you nothing needs to be changed.

BUT - 
You do need gptsync (a.k.a. the “Partitioning Tool” entry in the rEFIt menu) after using a partitioning tool that doesn’t know about the hybrid format, e.g. GNU parted or old versions of Disk Utility from a pre-10.4.6 Mac OS X boot CD.


---

### Post by demyers on 2007-08-11
> **pxwpxw said:**
> You could download the refit bootable CD iso,  to run gptsync. That might fix it without the full macosx reinstall.
One of the things I tried was installing gptsync while running from the CD, but gptsync said the disk was MBR only.

> **benanzo said:**
> I would try installing OS X and running all the updates. 
Good suggestion.  I had not tried booting the preinstalled OS X before overwriting it, so I reinstalled it and installed the updates (there were only 3, and none were related to firmware).  Then I installed and ran Boot Camp in case it might alter the firmware in some way.  Finally I reinstalled Feisty, this time the 64-bit version, but I ended up with the same result (white screen, then video shuts off).

Next I think I'll try a dual-boot installation (OS X + Boot Camp + rEFIt).

Thanks for the suggestions.

---

### Post by demyers on 2007-08-11
> **demyers said:**
> Next I think I'll try a dual-boot installation (OS X + Boot Camp + rEFIt).
This appears to be working, although the rEFIt boot menu didn't show up until the second time I rebooted the system.

Without rEFIt, I still couldn't boot Feisty.  After running Boot Camp and installing Feisty, if I held down the Alt key while booting I would get the option to boot "Windows", but selecting it left me in the same place I was before (video off, system stopped).

But it looks like I'm good to go with rEFIt.

---

### Post by cyberdork33 on 2007-08-11
Hmmm... something the EFI needs to intitialize, video or something.

---

### Post by entangled on 2007-08-12
Just a possibility...
I've had that symptom when I had a powered USB drive plugged in to my Mini with no boot media present in the drive. Unplugging it, or powering off, allows the boot.

---

