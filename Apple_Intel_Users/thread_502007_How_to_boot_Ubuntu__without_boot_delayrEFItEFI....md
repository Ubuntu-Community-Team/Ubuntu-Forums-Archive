---
title: "How to boot Ubuntu  without boot delay/rEFIt/EFI..."
date: 2007-07-16
forum: Apple Intel Users
---

### Post by thully on 2007-07-16
I've been experimenting with Ubuntu a lot on my MacBook lately, and decided to wipe OS X for the time being.  When I did this the first time, I was stuck with a boot delay while the system looks for an EFI-bootable partition.  However, the second time I did this, there was no delay, despite there being no GPT whatsoever on my drive.  

The secret - before you erase the drive, install Boot Camp in OS X and proceed like you are installing Windows. However, when it comes time to insert your Windows CD, insert your Ubuntu CD instead and proceed with the install, choosing the "Use entire disk" option.  After installing, you will be left with a Mac which boots straight into Ubuntu with no delay and without any GPT being used.  Essentially, it will act like a PC, sans fancy BIOS POST screens.  By doing this you can even install Linux distributions which traditionally don't play nice with the GPT, as you are now dealing with a simple, standard MBR and nothing else.  Granted, this wipes OS X off the drive - so it obviously isn't for everyone.  However, many here seem to be using primarily Ubuntu, and you can always install OS X to an external drive.

Furthermore, if one does this, and *doesn't* wipe OS X, Ubuntu will be the default boot after you install (Option key will be required to boot OS X) until you access the Startup Disk preference panel, at which point it won't see Ubuntu and will default to OS X.  If my intuitions are right, you can *also* change the default boot to Ubuntu - or change it back if it got switched -  by setting a bootable Ubuntu CD as the default and removing the CD before boot.  Doing this should enable "legacy boot", which is what is actually done if you set "Windows" as the default boot in Boot Camp.

(Honestly, I don't think I'm going to leave it this way - as a matter of fact, I may just load OS X back up as my primary OS and use VMware Fusion.  However, I still find this all interesting, especially as someone who has never liked rEFIt).

---

### Post by cyberdork33 on 2007-07-16
you don't have to have a GPT for OSX either. It will run fine off a MBR only drive. It just won't install to a MBR disk.

---

