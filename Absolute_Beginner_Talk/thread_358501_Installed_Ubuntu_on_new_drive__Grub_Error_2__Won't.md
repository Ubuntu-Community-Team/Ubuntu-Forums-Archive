---
title: "Installed Ubuntu on new drive / Grub Error 2 / Won't boot"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Mega_Fauna on 2007-02-10
Hi, 

This is my second weekend attempt to install Ubuntu and I'm still having problems.

**The Present Problem**: When I get past the Dell boot screen and hit F1 to continue, I get "Grub Error 2".

**Failed Solution**: I tried reinstalling Grub as instructed by this thread: [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

**What I did to get here**:

Took out XP drive and set ntfs data drive as single master by removing plugs.

Read up on partitions and installed the system several times on far side of ntfs partition. After several tries manually partitioning the drive the system still wouldn't boot w/o the live DVD.

Risking my data (it is alone on the backup drive now), I told the installer to wipe the drive and install as it saw fit, I ditched any manual attempts and went with the automatic install. The system now booted into Grub (which it didn't reach previously) but now gives me "Error 2".

Please help, I'm out of ideas and skill.

Thanks,

---

### Post by Mega_Fauna on 2007-02-10
More info (why won't it keep my edits?)

Just before the Grub error I am told that the system doesn't recognize the primary drive, then Grub boots and give me Error 2


**Just in cast this helps:**

ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24133   193848291   83  Linux
/dev/hda2           24134       24321     1510110    5  Extended
/dev/hda5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by Mega_Fauna on 2007-02-11
Close this thread, I rewrote it and opened a new one.

Thanks,

---

