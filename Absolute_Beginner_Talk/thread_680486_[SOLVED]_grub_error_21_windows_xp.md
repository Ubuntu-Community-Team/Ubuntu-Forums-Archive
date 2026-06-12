---
title: "[SOLVED] grub error 21 windows xp"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by dennycraig on 2008-01-28
I am have a partitioned computer-windos xp on one side and am installing ubuntu 7.04 (AMD64) on the other side. When I try to reboot after installing from the CD I get:

GRUB loading, please wait...
Error  21. 


I do not know what this means or how to fix it. I do know that I can not access my Ubuntu install nor my Microsoft side at all right now.

---

### Post by dcstar on 2008-01-28
> **dennycraig said:**
> I am have a partitioned computer-windos xp on one side and am installing ubuntu 7.04 (AMD64) on the other side. When I try to reboot after installing from the CD I get:

GRUB loading, please wait...
Error  21. 
........

Try this:

[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

As well, Ubuntu 7.10 AMD-64 is preferable to the 7.04 version (by most accounts of those that use the AMD-64 version).

---

### Post by dennycraig on 2008-01-29
> **dcstar said:**
> Try this:

[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

As well, Ubuntu 7.10 AMD-64 is preferable to the 7.04 version (by most accounts of those that use the AMD-64 version).

Thanks for the quick reply. 

The page you sent me to had two different options as to how to go about this. The first option, I tried and had gotten to the terminal window and typed in 'grub' but had difficulty trying to figure out how to translate harddisk + boot partition numbers for the grub. The example given was not very informative for a newbe. So I have not figured out how to translate yet. 

The other option on that page does not seem to describe what I find when I go into my installation CD. So the process does not make much sense given what I encounter when I boot the CD. It would make sense if things describes where what I saw. 

I'm still scratching my head. Not knowing what to try next. Any suggestions are appreciated.

---

### Post by oedha on 2008-01-29
error 21 can be 2 possibilities
1. your linux was deleted
2. your linux(grub) was not installed perfectly

what if you restore the Grub back.....you can check on my blog :
[http://oedha.blogspot.com/2007/11/bring-back-missing-grub.html](http://oedha.blogspot.com/2007/11/bring-back-missing-grub.html)

regards;
~E~

---

### Post by dennycraig on 2008-01-30
My grub going out happened after I had a power outage. That is why I was trying to reinstall my Ubuntu OS. But reinstalling the OS does not seem to do anything about the grub. I tried your suggestion but when I get to "find/boot/grub/stage1" my terminal responds with"Error 27: Unrecognized command". 

My Terminal's 'Minimal BASH-like editing support' may need a different set of commands. I have no idea. I just know that I tried it many times and it keeps coming back with the same response. 

What do you think?

This is an interesting way to learn about my system.

---

### Post by dennycraig on 2008-01-31
Okay, I took a days break from this to let my frustration level go down and to go to work. And I found that I only needed a space between 'find' and '/boot/grub/stage1' to make it work. The printing is so small that it was hard to see that I needed the space. So then I was able to run the command line as your given example and it was successful. Yet, when I rebooted I still got the same error message. 

So I have had some success at playing with command line but still none with my major concern of error 21 and not being able to boot.

---

### Post by dstew on 2008-01-31
Just to be sure I understand, you have installed Ubuntu onto a hard drive, and when you reboot the system the error message is simply "Error 21" with no further explanation? So you did not see the grub menu with its choices, correct? If so, this is probably a grub stage 1.5 error. This can be fixed.

---

### Post by MADMAX22 on 2008-02-01
> **dstew said:**
> Just to be sure I understand, you have installed Ubuntu onto a hard drive, and when you reboot the system the error message is simply "Error 21" with no further explanation? So you did not see the grub menu with its choices, correct? If so, this is probably a grub stage 1.5 error. This can be fixed.

How do you fix this?

I am wondering because after I install or attempt to install that is the exact thing I get first it says grub stage 1.5 then below that it says grub error 21 

I am trying to install on a hdd and I have vista on raid 0 with two other hdd;s. 

Thanks

---

### Post by dstew on 2008-02-01
Each case is different. The essential problem is that when grub was installed, the stage 1.5 was set-up to get grub stage 2 from a disk that is no longer there (or may not have been there to begin with -- that is, the installation was mis-directed). I don't mean that the disk has disappeared of course, only that the disk enumeration changed between the time grub was installed, and when the error occurred. There are many causes for a change in enumeration. It can change boot-to-boot depending on BIOS settings, and depending on the disk configuration of the hardware. Even plugging in an external drive can change it, in some BIOSes. You see this error most often when a user installs but tries to protect his or her Windows partition from grub. Sometimes the user will remove the drive that contains the Windows partition from the computer, then put it back in later.

This error seems to happen a lot with SATA drives, probably because the enumeration schemes were created after grub was created, so sometimes grub does not get it right. Grub is, unfortunately, no longer being worked on actively, and I think it is showing its age.

That said, the solution to the problem is to re-install grub. One has to be careful to get the disk enumeration right when re-installing, and then not change anything, including boot order, after grub is installed. You can re-install grub from a command line from a Live CD boot, or from the Supergrub disk. You can also make a grub floppy, and install using that. In all cases, the best way is to get the grub command line (with the grub> prompt) and enter the instructions. Using the command **grub-install** is fraught, especially in a system that is unusual in some way. It is better to use the **root** and **setup** commands.

One more thing: the Live CD is not good at recognizing RAID devices. If you have a RAID, it is better to use the Alternate Install CD. Also, grub I think will not recognize a RAID in most cases, but I am not sure about that.

If you want to reinstall grub, let me know, and we can try to work throught it together.

---

### Post by dennycraig on 2008-02-01
In response to the questions on post #7 by dstew. I had windows xp on one of my hard drives and I had ubuntu on another hard drive. They were both successfully running. Then I had a power outage while my computer was running. Afterwards I could get the grub menu but I could only boot up the windows side of my computer even though the ubuntu side showed. 

A friend suggested that I try reinstalling ubuntu. So I did. After reinstalling ubuntu I no longer got the grub menu. The only way I have been able to get into my windows side of my computer is with Super Grub. But even with that I still can not get into my, now reinstalled, ubuntu because of Error 21.  

It does say that it is grub stage 1.5 error, and says Error 21 below that. 

I tried to reinstall with a different copy of ubuntu 7.04 but the live  cd could not get past the error 21. 

I am now downloading an alternate install cd. 

I know virtually nothing about command line. But I am willing to try. I will probably try to install the alternate install cd to see if it can do anything. If there is any command line work needing to be done then I will need help.

---

### Post by dennycraig on 2008-02-02
I tried to install the alternate install CD but got the grub same error 21 at stage 1.5 before I could even do anything with the install. So it seems I must try some more command line. I'm not sure if I should do this from the super grub or from  the live cd which does get past the error. And when I do get into the command line I'm not sure what commands I should be giving. Any suggestions?

---

### Post by dstew on 2008-02-02
It is possible the hard disk partition that grub is trying to access has errors on it. This can happen if the disk was being written to when the power went out. You can check the disk for errors using the fsck command. Boot an Ubuntu Live CD, open the terminal, and enter the command```
sudo fdisk -l
```Post the output to the forum. You can run the fsck command on the partition that might have the errors, which should have an ext3 format. For example, if the Ubuntu Linux partition is /dev/sda2, the command would be```
fsck -a /dev/sda2
```

---

### Post by dennycraig on 2008-02-04
I put in the code: sudo fdisk -l and got 


Disk /dev/hda: 41.1 GB, 41110142976 bytes
240 heads, 63 sectors/track, 5310 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5310    40143568+   7  HPFS/NTFS

Disk /dev/hdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3736    30009388+   7  HPFS/NTFS

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       19365   155549331   83  Linux
/dev/hdd2           19366       19457      738990    5  Extended
/dev/hdd5           19366       19457      738958+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by dstew on 2008-02-04
From the Live CD command line, enter```
fsck -a /dev/hdd1
```

---

### Post by dennycraig on 2008-02-04
I entered the fsck -a /dev/hdd1 and got:


ubuntu@ubuntu:~$ sudo fsck -a /dev/hdd1
fsck 1.40-WIP (14-Nov-2006)
/dev/hdd1: clean, 97494/19447808 files, 1146081/38887332 blocks



Was this just an informational command? I'm wondering because nothing seems to have changed in regards to my computer's concern. I hope this is helpful.

---

### Post by dstew on 2008-02-04
No, the fsck command examines a partition for file system errors, such as bad blocks, and fixes them if it can. This shows that there are no errors on /dev/hdd1, which is good to know. Now we can try to reinstall grub. From the Live CD system, open a terminal window and enter the command```
grub
```This should give you the grub command line, with the **grub>** prompt. At the grub> prompt, enter the command```
find /boot/grub/stage1
```Post the result to the forum.

---

### Post by dennycraig on 2008-02-04
Here is what I got:

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,0)
grub>

---

### Post by dstew on 2008-02-05
Now we need to re-install the grub boot loader so that the stage 1.5 will be able to find the directory that has stage1 in it (and also stage2, which is what we really need). Now, just to be sure, you have your system arranged so that you use the Vista boot management program, and choose Ubuntu from that, correct? Then you get the grub error. If that is true, then we need to install the grub boot loader into the boot sector of the /dev/hdd1 partition.

If what I said above is true, re-install grub this way. Boot the Live CD, open the terminal and enter grub. On the grub command line, enter these commands:```
root (hd2,0)
setup (hd2,0)
quit
```Then reboot. If what I said above is not true, let me know and I will give you further instructions.

---

### Post by dennycraig on 2008-02-05
First, I am using xp and not vista. Not sure if that is of any importance. 

Second, as far as boot management programs go, I am not sure. I set this up a while ago with the help of a friend who is out of town at this time. Is there some way we can check on this as I do not want to give you incorrect information?

---

### Post by dstew on 2008-02-05
I think I misunderstood your situation. I remebered that you were booting Windows, but looking back I see you were using the supergrub disk to boot it. So, you have XP installed, and it boots using the supergrub CD, and you have installed Ubuntu, but when you boot in the regular fashion, you get the grub error.

In that case, the grub setup commands should be:```
root (hd2,0)
setup (hd0)
quit
```That should bring up the grub menu when you reboot. We might then have to edit the grub menu to get everything finished.

---

### Post by dennycraig on 2008-02-05
I entered the commands you suggested and here is the computers' response:

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 


I tried rebooting and got the same stage1.5 error 21 message.

---

### Post by dstew on 2008-02-06
Boot the live CD, and enter **sudo fdisk -l** again. Maybe the partitions have changed since your last installation. Post the result.

There is another possibility, that your BIOS has been set to boot a partition rather than from the MBR of the first disk. Please check in your BIOS for the boot device.

EDIT: Looking back over the thread to see if there are any more clues, I have noticed something odd. Your original fdisk output showed the disks hda, hdb and hdd, but no hdc. This is strange. Grub seems to be content finding its root in hdd, which in grub-speak is (hd2). However, the fact that there is no hdc in your system means that grub might have originally installed in the presence of an hdc drive (an external disk perhaps?). In that case, it might have a device.map file that says that (hd2) is actually hdc. So, in addition to posting your fdisk output, please also post the output of```
cat /boot/grub/device.map
```

---

### Post by dennycraig on 2008-02-06
Here is what I got with the fdisk -l code:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
240 heads, 63 sectors/track, 5310 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5310    40143568+   7  HPFS/NTFS

Disk /dev/hdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3736    30009388+   7  HPFS/NTFS

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       19365   155549331   83  Linux
/dev/hdd2           19366       19457      738990    5  Extended
/dev/hdd5           19366       19457      738958+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


Here is what I got when I entered the cat command.I'm not sure if I entered it correctly or not because of the reply. But then you will be able to see what I entered:



ubuntu@ubuntu:~$ cat boot/grub/device.map
cat: boot/grub/device.map: No such file or directory
ubuntu@ubuntu:~$ 


You also asked me to check in my BIOS for the boot device. I went into the Advance BIOS feature and saw boot devices listed 1st, 2nd, 3rd. I'm not sure what I was suppose to be looking at or at. Or what to tell you from what I see? Hope this is helpful. 

Thanks for the time and effort

---

### Post by dstew on 2008-02-07
> Here is what I got when I entered the cat command.I'm not sure if I entered it correctlyMy fault. I forgot to tell you that to run that command from the Live Cd you need to mount the hard drive partition onto the Live CD file system. Here is how you do that. From the Live CD system, open a terminal and enter the command```
sudo mkdir /mnt/hard_disk
```That creates a "mount point" directory for your hard disk. Now, mount the hard disk partition /dev/hdd1 to the mount point you created with the command```
sudo mount -t ext3 /dev/hdd1 /mnt/hard_disk
```To access files on the hard disk, you start in the /mnt/hard_disk directory. So, to get the device.map file, the command would be```
cat /mnt/hard_disk/boot/grub/device.map
```

Knowing how to mount the hard disk partition onto the Live CD is important for debugging lots of boot problem. For example, if we need to edit /boot/grub/menu.lst.

---

### Post by dennycraig on 2008-02-07
Here is what I got when I entered the codes:

ubuntu@ubuntu:~$ sudo mkdir /mnt/hard_disk
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdd1 /mnt/hard_disk
ubuntu@ubuntu:~$ cat /mnt/hard_disk/boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdd
ubuntu@ubuntu:~$

---

### Post by dstew on 2008-02-07
The device.map file seems correct.

Here is one more thought (and I am fast running out of them).  I notice that you have two bootable Windows partitions. It could be that your BIOS is set to boot one of the partitions, and it is possible that on that partition you accidentally installed grub before, and that copy of grub is giving you the error. Go into your BIOS again and look carefully at your boot disk settings. If possible, make sure that the BIOS is set to boot the first hard disk (40 gb) because that is where we last installed grub, and so far I don't see that we made any mistakes with the last installation. Also, try to see if it is booting from the first hard disk MBR, and not directly booting the partition. Some BIOSes have the ability to boot partitions.

---

### Post by bbt5001 on 2008-02-08
dstew wrote:

> Here is one more thought (and I am fast running out of them). I notice that you have two bootable Windows partitions. It could be that your BIOS is set to boot one of the partitions, and it is possible that on that partition you accidentally installed grub before, and that copy of grub is giving you the error. Go into your BIOS again and look carefully at your boot disk settings. If possible, make sure that the BIOS is set to boot the first hard disk (40 gb) because that is where we last installed grub, and so far I don't see that we made any mistakes with the last installation. Also, try to see if it is booting from the first hard disk MBR, and not directly booting the partition. Some BIOSes have the ability to boot partitions.

Spot on! I just ran into this grub failure yesteday (I normally run Gentoo, but needed one system that was more user-friendly, so tried to quickly set up a dual-boot XP/Ubuntu system).  It turns out that the BIOS had my second hard drive disabled. I set the slave drive from OFF to Auto, rebooted back into the BIOS, and this time the 2nd hard drive appeared. Booted again, and the Grub selection menu appeared! It's been a very frustrating week, and this one small success at the end tickled me, probably more than it should have.

dennycraig, I hope this works for you, too.

---

### Post by dennycraig on 2008-02-12
Thank you everyone for helping me with this concern. I seemed to have fixed it. In my running around in my bios I saw a fail safe defaults option. I reset the  BIOS to the fail safe defaults. That seemed to have re-ordered the boot disk order. I can now see my grub menu and can chose to boot up Ubuntu or Microsoft. 
thank you

---

### Post by dstew on 2008-02-12
Great. Please mark the thread as Solved (in your Thread Tools menu.)

---

### Post by mastermatt63 on 2008-06-03
hey guys, man i really hpoe someone is reading this. n e ways i installed ubuntu last night bby partitioning my external USB Drive. When I boot up i get the same problem that denny had. error 21. but on my Sony VAIO FZ140, i can't change my off and auto settings, atleast i don't think so. I think I can get into the CMOS by holding down f2 at start-up, but how can i get into BIOS to change the off and auto settings for my drives? Thank you very much in advance. by the way,this is my first time even trying Linux.

---

### Post by arashispencer on 2008-06-19
I AM having the same problem but worse. I have error 15,17 and 21

---

