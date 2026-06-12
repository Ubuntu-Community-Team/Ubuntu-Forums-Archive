---
title: "Corrupt install or no?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by C00P88 on 2007-08-15
Hello all,

After several attempts at burning the iso CD, I could never burn one that did not pass the "check CD for errors" test at the Ubuntu main menu. So I decided to install anyway, thinking the worst that would happen would be me starting over. The CD actually installed Ubuntu, but now I wonder if my install is corrupt, or will the automatic update feature correct any errors? When I tested the iso CD, the test said it found errors on 85 files. How can I check to make sure Ubuntu is not corrupt, or is this an all-or-nothing deal (it either works or it doesn't?)? 

Thanks for reading.

Coop

Edit: I just noticed there's an hdc1 icon on the desktop, is this supposed to be there? I'm used to the "trash can". Just hoping nothing is messed up.

---

### Post by Rocket2DMn on 2007-08-15
hdc1 would be another partition on your hard drive.  Did you setup a dual boot or do you have some sort of data partition?

If Ubuntu installed OK, then you are probably fine, but for future reference, you should always check the md5sum of the .iso file after downloading before you burn it to a disc.  This will ensure that the file downloaded correctly.  Once that checks out, you should burn at a slow speed (like 4x) to prevent write errors, and use quality media if possible.
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM") md5sum
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against (for Ubuntu only)

If you have the time and want to feel good about the install, you can try redownloading/reinstalling and following those suggestions.  If everything checks out, you can live with peace of mind :)

Welcome to Ubuntu!

---

### Post by C00P88 on 2007-08-15
Wow, that was a fast response! I did the checksum/hash test on the iso file a few times, and it always checked out(md5Sum). However, I've never been able to burn an error-free boot disk. I've been burning at 4x, which is the lowest setting my optical drive supports. I've also tried burning with Nero, and Infrarecorder. I tried different media types, TDK, Sony, Maxell, Imation, to no avail. Not sure what I'm doing wrong.

This is a dual boot, with Windows XP. I used the manual partition option, and in the newly created free space I made a 2000mb swap partition, and then another partition with the remaining 20gig. Had to put a "/" in the mount field for some reason. So my hard drive has a total of 3 partitions, including the windows partition. 

Ok, I took a look in the hdc1 icon, it looks like it's my windows partition. Is this normal? :confused:

---

### Post by Rocket2DMn on 2007-08-15
It is normal.  Assuming the windows partition is in NTFS format, you will need to install ntfs-3g to write to it (if you want).  Otherwise just leave it alone.
More info about that can be found here:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G) - I suggest the automatic way for this.
Help here for adding the partition to fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

