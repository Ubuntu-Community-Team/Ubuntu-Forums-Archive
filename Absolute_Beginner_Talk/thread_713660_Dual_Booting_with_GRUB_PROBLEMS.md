---
title: "Dual Booting with GRUB PROBLEMS"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by parkerfutbol3 on 2008-03-03
Ugh this is really driving me nuts! I successfully installed Ubuntu (7.10) on my Dell. My setup is two 250GB hard drives, the first of which has only Windows, the second has 200GB for extra backup space for Windows, the final 50GB of space on the second disc has Ubuntu installed on it. Everything installed great and I was super excited to finally have Ubuntu running on a powerful computer. 

I go to reboot and in the BIOS I get an error of GRUB error 22. I forget the exact wording but in all of the forums out there that has information about grub error 22 it has not helped me a bit. Apparently it means GRUB can't find the partition. I also tried using the liveCD to change the GRUB setup [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")Please if you have any knowledge try and help me out.

Thanks in advance!

---

### Post by bumanie on 2008-03-03
Could you please post the output of > sudo fdisk -l 

---

### Post by parkerfutbol3 on 2008-03-03
I cannot get into Ubuntu for GRUB wont allow me to choose a system to boot (I should note that ONCE it worked after numerous attempts, it never has since though). Are you saying I should use the livecd?

---

### Post by bumanie on 2008-03-03
Sorry, I got interrupted after I read the guide you followed and forgot about the grub 22 error (I tried to stop it  posting  but it had gone too far when I realised my mistake). When you followed the guide on the thread, what (hd?,?) did you use? According to what you originally posted, you should be sending grub to (hd1,1). If you sent it to (hd0,1) as on the guide, it won't work with your setup. Follow the same procedure, and substitute 
root (hd1,1)
setup (hd1)
quit
That should work. If it doesn't, read this [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
that is an exstensive guide to grub.

---

### Post by parkerfutbol3 on 2008-03-03
OH! That makes complete sense as I was sending it as the guide said to (hd0). However when I do the find /root/grub/state1 command it does say it is in (hd1,2)... is that significant because I do also have a windows partition on this disk as well.

Thanks for everthing

---

### Post by parkerfutbol3 on 2008-03-03
Also I will post my fdisk -l output for anyone that wants to help

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30393   244131741    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f2ded8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6       48163+  de  Dell Utility
/dev/sdb2               7       24322   195318270    7  HPFS/NTFS
/dev/sdb3   *       24323       30143    46757182+  83  Linux
/dev/sdb4           30144       30394     2016157+   5  Extended
/dev/sdb5           30144       30394     2016126   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)
```

---

