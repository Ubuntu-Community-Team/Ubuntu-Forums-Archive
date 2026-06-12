---
title: "Looking for Ubuntu 16.04 Desktop amd64+mac"
date: 2016-06-30
forum: Apple Hardware Users
---

### Post by feipoa on 2016-06-30
I have a Mac Pro Quad Core 2.0 Original from 2006.  It has EFI 32-bit and requires 32-bit booting.  The system contains 64-bit Intel Xeon 5130 CPUs.  When I use Ubuntu 16.04 (Xenial Xerus), desktop+amd64 to create a DVD image, then boot the Mac, the system hangs at asking me to select 1 or 2 for DVD type or something of that nature.  I cannot select 1 or 2.  I read some tricks online which say to hold the 1 key down once the DVD starts booting, then press return when the screen turns black, then hit return again.  While this selects 1, the return function doesn't advance the installation.  Other online tricks include some magic with the option key.  Nothing works.  Further reading online pointed to needing the +mac iso image.  I can only find the +mac version for Ubuntu 14.04.  Further reading suggests making some modifications while running Mac OS X.  I do not have Mac OS X installed -  my HDD is empty.Where can I find ubuntu-16.04-desktop-amd64+mac.iso ?  Alternately, what is the fastest method for installing the latest Ubuntu on this system?  Thanks!

---

### Post by howefield on 2016-06-30
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by feipoa on 2016-06-30
I created a bootable DVD from ubuntu-14.04.3-desktop-amd64+mac.iso.  This amd64+mac image works on my Mac Pro.  I will try fully updating 14.04 then try updating to 16.04.  When will the 16.04 amd64+mac iso be available?

---

### Post by feipoa on 2016-07-01
14.04.**3** caused some issues when going to upgrade to 16.04 - I updated 14.04 with all updates for this system, but it didn't give me the option to upgrade to 16.04.  It wanted to upgrade to 15.10, which didn't work.  The screen went blank at some point and wouldn't turn back on.

I then created a DVD with ubuntu-14.04.**4**-desktop-amd64+mac.iso.  I updated 14.04 with all 14.04 updates.  At which point, it gave me the option to upgrade to 16.04.  I am now using 16.04 on my Mac Pro without issue and it is updated.  The process took a long time.  When can we expect to see the +mac iso image of 16.04-LTS, e.g. ubuntu-16.04-desktop-amd64+mac ?  

Thanks.

---

### Post by howefield on 2016-07-01
> **feipoa said:**
>  When can we expect to see the +mac iso image of 16.04-LTS, e.g. ubuntu-16.04-desktop-amd64+mac ?

Probably a long wait, so don't hold your breath...

[https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install](https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install)

---

### Post by keith-k on 2016-09-20
Went ahead and followed that guide (  [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16) ) It worked. For 16.04.1 [https://drive.google.com/file/d/0BxsSnrY3p_qbUktQU2hNa0dJM1E/view?usp=sharing](https://drive.google.com/file/d/0BxsSnrY3p_qbUktQU2hNa0dJM1E/view?usp=sharing)

---

### Post by feipoa on 2017-03-11
Are there any issues with using said system (Mac Pro Quad Core 2.0 Original from 2006 containing 64-bit Intel Xeon 5130  CPUs; has EFI 32-bit and  requires 32-bit booting) and cloning the hard drive?  I'm trying to upgrade the hard drive on my system, which is a slow and noisy 80 GB SATA drive with a 1 TB hybrid SATA drive.  All I want to do is clone the drive, then remove the old drive, and move the new (cloned) drive into the drive bay of the old HDD.  I have read a few forum threads and have tried using dd.  The clone seemed to have worked, but after booting with the new HDD, the drive boots to a command console with (initramfs), saying something about the root filesystem on /dev/sda2 requiring a manual fsck.  Also noted an "unexpected inconsistency.  And:  superblock needs_recovery flag is clear, but journal has data.  Run journal anyway.

I'm still relatively new to Ubuntu and have not been able to figure out why I am getting that error after cloning the HDDs with dd.  Since I cannot boot to USB or most non+mac CD's on this system, I then removed the two HDD's and put them in my Opteron 185 system and booted Clonezilla with a live CD.  I cloned the drives this way, put them back into the MacPro, but could not boot from the cloned drive.  The system was asking for a HDD or something.  I'm now going to try ddrescue from the Ubuntu 14.04 live CD to clone yet again.  

I thought this would be a really simple operation, so I am left wondering if there is some issue cloning HDDs with this Mac Pro system?  I have spent so much time on this by now that I could have reinstalled Ubuntu 14.04 and upgraded to 16.04 again.  I am trying to avoid that still so that I don't have to reinstall everything.

EDIT: 3rd time's a charm.  I was able to successfully clone and boot the HDD with ddrescue, e.g. sudo ddrescue -v --force /dev/sda /dev/sdb.  I guess now I'll look into how to use gparted with the live CD to figure out how to increase my file system size.  The clone kept my filesystem size the same as with the 80 GB drive.

---

### Post by nanook2 on 2017-04-22
> **keith-k said:**
> Went ahead and followed that guide (  [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16) ) It worked. For 16.04.1 [https://drive.google.com/file/d/0BxsSnrY3p_qbUktQU2hNa0dJM1E/view?usp=sharing](https://drive.google.com/file/d/0BxsSnrY3p_qbUktQU2hNa0dJM1E/view?usp=sharing)

I can confirm that this program also works for Ubuntu Mate 17.04 and this is a tremendous relief since if my old Mac Pro 1,1 got scribbled past where it could boot, with no rescue disk, I'd be forced to reload 12.04 and upgrade back to current, a real pain, almost like reloading Windows.  These old machines have adequate horsepower to still make good workstations, especially if you upgrade the video card to something more capable and max out the memory (which officially is 32GB but I have heard from some folks they were able to successfully use more).  Memory Masters has 32GB for $39 for the Mac Pro 1,1 and 1,2.  I've got 32GB in my quad xeon and the performance is quite usable, much more so than it was under MacOS Lion which was, to put it mildly, painful!

---

### Post by nanook2 on 2017-04-22
Regarding using ddrescue to clone a drive to a larger drive, I've done this also and gparted makes increasing the file system size a breeze.  Just use the resize option, commit the change, wait a few minutes for it to do it's work and you're good.  It is a good idea to run fsck after you finish to make sure the file system is clean.

---

