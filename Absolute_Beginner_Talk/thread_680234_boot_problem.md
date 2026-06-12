---
title: "boot problem"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by baconmaker on 2008-01-27
I received my Ubuntu 7.10 disk on Friday and installed it on an old Compaq Deskpro EN with an Intel 1.0 processor with 256 ram.  Everything went well.  Started playing on Saturday installed Firestarter, avast antivirus, wine, crossoffice, and thunderbird because I had some problems with Evolution mail.  Everything seemed to be going well but I could not get my windoze programs (which I need) to work.  Decided to uninstall wine, crossoffice and evolution and just play around learning more of Ubuntu.  In the process of trying to get Quickbooks to work my cd-rom stopped mounting anything, windows disks, audio disks, and Ubuntu install disk.  I thought my cd decided it was the appropriate time to die.  Figured I would replace it on Sunday.  Tried to boot up on Sunday and I get to the login screen and login as normal and then I just sit there looking at an auburn screen.  I try to boot using recovery mode and I get to a point where I am told that firestarter failed to start and then it stops and waits for a command which I am clueless to provide.  I am beginning to think I have two problems.  1) I deleted something which I should not have and thus no boot. 2) My cd-rom died thus I cannot reinstall and start over.  The cd does open/close and the light goes on but I never hear the disk spinning.  My questions  1) does it seem like I might be barking up the right tree with my assessments?  2) would anyone have any idea what command I might need to boot in recovery mode?  Thank you for your help.

---

### Post by Kilz on 2008-01-27
> **baconmaker said:**
> I received my Ubuntu 7.10 disk on Friday and installed it on an old Compaq Deskpro EN with an Intel 1.0 processor with 256 ram.  Everything went well.  Started playing on Saturday installed Firestarter, avast antivirus, wine, crossoffice, and thunderbird because I had some problems with Evolution mail.  Everything seemed to be going well but I could not get my windoze programs (which I need) to work.  Decided to uninstall wine, crossoffice and evolution and just play around learning more of Ubuntu.  In the process of trying to get Quickbooks to work my cd-rom stopped mounting anything, windows disks, audio disks, and Ubuntu install disk.  I thought my cd decided it was the appropriate time to die.  Figured I would replace it on Sunday.  Tried to boot up on Sunday and I get to the login screen and login as normal and then I just sit there looking at an auburn screen.  I try to boot using recovery mode and I get to a point where I am told that firestarter failed to start and then it stops and waits for a command which I am clueless to provide.  I am beginning to think I have two problems.  1) I deleted something which I should not have and thus no boot. 2) My cd-rom died thus I cannot reinstall and start over.  The cd does open/close and the light goes on but I never hear the disk spinning.  My questions  1) does it seem like I might be barking up the right tree with my assessments?  2) would anyone have any idea what command I might need to boot in recovery mode?  Thank you for your help.

start in recovery mode, type in ```
sudo apt-get -f install ubuntu-desktop
``` then hit enter. You might have removed the desktop when you removed evolution.

---

### Post by baconmaker on 2008-01-28
I tried your command and I thought I made some progress.  But then it stopped with this command

E: Unable to fetch some archives, mayby run apt-get update or try with --fix-missing?

Tried both of the commands.  Several lines flash before me, mostly with these statements:

Failed to fetch...   Could not resolve...   and finished with 

E: Some index files failed to download, they have been ignored, or old ones used instead.

Turned off computer to try and reboot normally--no change.

Tried booting off of Ubuntu disk in cdrom--no success. (I change cdrom's)

---

### Post by baconmaker on 2008-01-28
Failed to add this.  There is nothing valuable on this computer, so if I have to do a complete reinstall off the cd there is no harm done.  Just things learned.  But I also cannot get the cdrom to mount anything.

Just taking a flier here.  Could I change my boot order to floppy first and get something on floppy to wipe the hard drive, then change back to cdrom first and hope that it mounts the install disk?

---

### Post by logos34 on 2008-01-28
> **baconmaker said:**
> Could I change my boot order to floppy first and get something on floppy to wipe the hard drive, then change back to cdrom first and hope that it mounts the install disk?

you could try Darik's Boot and nuke or Active KillDisk

---

### Post by baconmaker on 2008-01-29
Used Darik's boot an nuke to wipe the hard drive successfully, but I still cannot get the cdrom to mount anything.  thanks for your help.

---

### Post by baconmaker on 2008-01-29
Well I am back in business.  I changed the jumper settings on my cdrom and everything seems to be working.  What I do not understand is how did it work in the first place?  Just thought I would let everybody know how my problem was solved in case it would help anyone else.  Thanks.

---

