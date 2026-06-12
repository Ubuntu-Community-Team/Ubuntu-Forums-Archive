---
title: "Grub/Boot.ini"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by daxLeet on 2007-06-07
I installed ubuntu and have had it for a while, then my brother needed XP so I installed a small XP partition, and it seems to have taken over the boot sequence.  When I boot it up, I no longer get the GRUB, it just loads Windows right away.  How can I revert back to GRUB, and how can I boot into my ubuntu partition?

Thanks.

---

### Post by southernman on 2007-06-07
You'll need to reinstall grub. Hold on while I go search the forums for you. brb

---

### Post by Inxsible on 2007-06-07
Because you installed XP after ubuntu, it simply overwrote the MBR. 
you will have to re-install grub. its tedious but it can be done. Search for it in the forums, there are lots of ppl who have done this and there are a few tutorials out there.

---

### Post by southernman on 2007-06-07
Ok, you'll need the livecd for this method... 

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

[edited]
[I]
If that one isn't enough for you. Check out [this page]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst"), it has a whole host of things you can do with grub. [/I]

[/edited]

---

### Post by Dedoimedo on 2007-06-07
Hello,

You could try Super Grub Disk to repair the GRUB. It's a preferred method if you are not comfortable with editing GRUB configuration file manually.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Dedoimedo

---

### Post by southernman on 2007-06-07
If there was a grub at all, they could do this. The fresh XP install took care of grub for them, now they have to reinstall grub. XP simply wrote over the MBR, so I don't see super grub as an option at this point.

---

### Post by Dedoimedo on 2007-06-07
Hello,

It will work. Super Grub Disk takes care of this. It even says so on the site... I have done this several times, personally. 100% success.

This can also be done manually.

Basically, you need to find Stage 1 and then set it up in MBR. Once stage1 is setup, it can then load Stage 2 and eventually boot your favorite OS. Stage 2 is usually located on the root partition of a Linux distro.

Here are the commands:

find /boot/grub/stage1

Let's assume it finds Ubuntu at partition hda3

Then:

root (hd0,3)
setup (hd0)
boot

This is all the magic to it. Very simple.

root tells where the grub config file is to be found and used.
setup will write the information to relevant target - in this case MBR.

Cheers,
Dedoimedo

---

### Post by southernman on 2007-06-07
hmphhhh! Downloading that puppy right now. 

Thanks for setting me straight! :P

edited/

For the record, the link you posted is having some problems according to [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk"), a temporary link is at [http://forjamari.linex.org/projects/supergrub/]("http://forjamari.linex.org/projects/supergrub/")

---

### Post by Najand on 2007-06-07
Better to use this:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)
I has a walkthrough to recover grub.

---

