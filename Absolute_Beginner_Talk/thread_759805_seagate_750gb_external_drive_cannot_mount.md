---
title: "seagate 750gb external drive cannot mount"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by mrchuckbadazz on 2008-04-19
I am on Ubuntu 7.10 and am really enjoying the switch from Windows. I find Ubuntu more challenging than Windows, But I like the freedom from M$. I am currently having an issue with my Seagate 750GB external HDD. Previously it was mounting and unmounting fine besides some issues here and there. Now it will not mount at all and I have rebooted and plugged the device in and unplugged it. I have read some of the other posts, But none of them have helped me. I have noticed that most users post their fdisk output.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7ca49d4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9565    76830831   83  Linux
/dev/hda3            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001    7  HPFS/NTFS


***

Also here is the error with screenshot. 

Cannot mount volume. 

Details 
$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sda1':input output error NTFS is either inconsistent, or you have hardware faults, or you have SoftRAID/FakeRAID hardware, In the first case you can run chkdsk /f on Windows then reboot into windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and moutn a different device under the /dev/mapper/ directory.  9e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details. 

I am open to installing Windows again if I have to and also I have about 100GB of data on this puppy I do not want to part with unless absolutely necessary. Thanks for any help in advance. Also a few other times I've had issues I have found my answer usually on these forums. you guys rock! :guitar:

---

### Post by quirks on 2008-04-19
It looks like the filesystem on your external HDD is corrupt. Unfortunately, NTFS is not supported very well on Linux yet. Therefore, I would really recommend doing a filesystem check under Windows as explained in the error message. Otherwise, you risk losing data.

It is a good practice to use FAT32 as a filesystem for external mass storage devices which are mounted in different operating systems. It is an out-dated filesystem, but on the other hand, it is widely supported.

---

### Post by Trollslayer on 2008-04-19
I have had this before, a parition that has been accessed by both Windos and Linux  has problems.

---

### Post by mrchuckbadazz on 2008-04-19
Dang. This really blows. Unfortunately all I have is a norton ghost backup of my windows XP installation. So now I am going to finish up some torrents, burn everything i want backed up to DVD and then install windows xp, and check my seagate drive. This is what I figured I would have to do. After all this is over though, I will be moving to fat32. Then I will partition xp on its own partition when installing ubuntu again and hope for no NTLDR problems!! I'll keep ya' posted.

---

### Post by mrchuckbadazz on 2008-04-26
I have finally had the time to delve deeper into this problem. :) I have burned all my remaining torrents. I am now on windows!! (blah). I am running the diskcheck. I have over 100 gigs of data in use on the drive so I figure this will take awhile. I was able to go directly into the drive from my computer and the folders were there, But I did not try accessing any individual files. Once the disk check is complete, Should I format to FAT32 or ext3? Is there any other file systems that I should consider?

---

### Post by catalina on 2008-04-26
Hi There,

If you are using the drive as an external drive in Windows and an external drive in Linux you have to make sure that you unmount it in Windows and Linux properly otherwise it will be caught in a loop thinking that it is mounted for the windows file system when you are on the Linux.

This happends with pen drives to me here and there.  You have to log back into Windows/linux (whichever file system you last used your hard-drive) and it will likely still be mounted, then you can unmount it properly.

Also, there is an NTFS configuration tool included in linux that makes it possible and easier to read and write to and from windows partitions.

If you are dual booting remember to install windows first!

Take Care,
Dean.

---

