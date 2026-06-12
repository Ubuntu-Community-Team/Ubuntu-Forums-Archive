---
title: "Backup Image with Partimage"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-08-09
I have the Feather Linux boot disk with Partimage on same and I am trying to back up as an image  my Ubuntu Dapper installation on my first hard disk at /dev/hdb1 in Ext 3 to a partition on another hard disk /dev/hda7 vfat. The installation is only 2.6 gigs. I have run Partimage from the bootdisk (Feather) but it doesnt seem to do anything. I think I may have to mount the receiving partition or both original and receiving or something. Can someone please advise me how to do this and how to mount the disks if necessary.:rolleyes: :confused: :?:

---

### Post by Frank Golden on 2006-08-09
> **Gerry Atric said:**
> I have the Feather Linux boot disk with Partimage on same and I am trying to back up as an image  my Ubuntu Dapper installation on my first hard disk at /dev/hdb1 in Ext 3 to a partition on another hard disk /dev/hda7 vfat. The installation is only 2.6 gigs. I have run Partimage from the bootdisk (Feather) but it doesnt seem to do anything. I think I may have to mount the receiving partition or both original and receiving or something. Can someone please advise me how to do this and how to mount the disks if necessary.:rolleyes: :confused: :?:
I am not familiar with Feather Linux but I use SystemRescueCD
which has partimage on it. See my guide here.

[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

Quickly you should have a terminal prompt when you boot
Feather Linux if it's anything like SystenRescueCD.
At the prompt type [mkdir /backup] without the brackets and
press enter. Then type [mount -t vfat /dev/hda7 /backup] again without the brackets. This mounts the drive you will copy to.
Now type partimage to open partimage GUI. Follow the instructions
in my guide for working with partimage. You cannot have the drive you copy mounted. Partimage will take care of the rest. 
Depending on your amount of ram and other hardware specsthe process could take a while. I have 2 GB of ram a Core Duo proc
and 5400 rpm HDD. I also save to my Fat32 shared partition
on the same drive my Ubuntu is on. So my 3.7 GB Ubuntu install
copies in about 12 minutes including SystemRescueCD boot up time.
Restore is even faster. When copying choose the option to reboot
when copying is successfully completed. Like shown in my guide.
Be patient. Even after the progress bar reaches 100% the program is still processing. If you interupt it it won't give you an error but if you later try to use it to restore Ubuntu, it will try to restore, overwriting your damaged Ubuntu
until it reaches the point where you interupted the image making
process and error out. You then will have no option but complete reinstall. If my instructions don't work with Feather
try downloading SystemRescueCD and using that.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

BTW, because my laptop can boot from anything including
USB flash drives, I used the instructions on the sysresccd
web site and installed on a 1 GB cruzer Titanium thumb drive.
Handy and quicker than CD.

---

### Post by Gerry Atric on 2006-08-12
> **Frank Golden said:**
> I am not familiar with Feather Linux but I use SystemRescueCD
which has partimage on it. See my guide here.

[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

Quickly you should have a terminal prompt when you boot
Feather Linux if it's anything like SystenRescueCD.
At the prompt type [mkdir /backup] without the brackets and
press enter. Then type [mount -t vfat /dev/hda7 /backup] again without the brackets. This mounts the drive you will copy to.
Now type partimage to open partimage GUI. Follow the instructions
in my guide for working with partimage. You cannot have the drive you copy mounted. Partimage will take care of the rest. 
Depending on your amount of ram and other hardware specsthe process could take a while. I have 2 GB of ram a Core Duo proc
and 5400 rpm HDD. I also save to my Fat32 shared partition
on the same drive my Ubuntu is on. So my 3.7 GB Ubuntu install
copies in about 12 minutes including SystemRescueCD boot up time.
Restore is even faster. When copying choose the option to reboot
when copying is successfully completed. Like shown in my guide.
Be patient. Even after the progress bar reaches 100% the program is still processing. If you interupt it it won't give you an error but if you later try to use it to restore Ubuntu, it will try to restore, overwriting your damaged Ubuntu
until it reaches the point where you interupted the image making
process and error out. You then will have no option but complete reinstall. If my instructions don't work with Feather
try downloading SystemRescueCD and using that.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

BTW, because my laptop can boot from anything including
USB flash drives, I used the instructions on the sysresccd
web site and installed on a 1 GB cruzer Titanium thumb drive.
Handy and quicker than CD.



Thanks Frank very much, solved all the problems.

---

