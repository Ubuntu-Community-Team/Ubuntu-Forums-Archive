---
title: "Is Windows still there?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Sulla158 on 2007-03-29
I'm pretty sure that I know the answer to this question already, but here it is.  If when I installed Ubuntu I chose the option to delete everything else on the harddrive that means everything including windows right.  I probably need to get windows back at some point so any suggestions on how to do that would be helpful.

---

### Post by raja on 2007-03-29
If you chose to delete everything, yes - windows is gone. If you have more than 500 MB RAM and need windows only infrequently, the easiest approach is to install windows in a virtual machine with vmware. If you want to dual boot, it is a little painful because windows will overwrite the MBR.

---

### Post by bodhi.zazen on 2007-03-29
Windows bye-bye

If you want to dual boot, boot to the live cd, fire up gparted, resize your ubuntu partition, make a FAT32 partition in free space.

Boot windows cd. Install into the FAT partition, reformat to NTFS as a part of the install.

Now the fun parts :

1. Download/install all your windows drivers. Install antivirus. Install firewall. Install antisypware.

[indent]Hope the drivers are on the windows CD or you know how to download them from the internet.[/indent]

[indent]Err ... Hope you did not have one of those new fancy restore partitions (rather then a windows CD) that you did not just over write ... In that case, Windows bye-bye, you will need to contact your computer manufacturer for restoration or buy a new copy of windows.[/indent]

2. Re-install grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

