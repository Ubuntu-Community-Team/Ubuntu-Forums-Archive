---
title: "Install Error Code 2"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by ksd123 on 2007-05-24
I recently installed Ubuntu from the downloadable disk. I previously had XP running on a AMD 64 system with RAID 0. I was unable to figure out how to "shrink" or repartition my drive to keep the old system intact, so I proceeded with the "guided" option of partition, which erases everything and starts new.

Everything went well with the install. When it was done i selected to restart the system. I removed the install cd from the drive. The system then went through the normal boot. Then I get the following before it even starts to load Ubuntu.

Boot from CD :
GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 2


At this point the system just stops. What is the deal? I sure hope this is something small, because if the installer couldnt even handle my simple system with RAID 0, this product will have problems in the future.

---

### Post by vtel57 on 2007-05-24
Boot to the Live CD session. Open a Terminal session (command line) and type the following command:

```
 $ sudo fdisk -l
``` 

Post the output of that command here, please.

By the way, is this a software RAID (fake RAID)? Did you have to load drivers from the manufacturer before creating the RAID? If so, Linux does not play well with software RAID. That may be one of your problems.

---

### Post by ksd123 on 2007-05-24
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150255913+  83  Linux
/dev/sda2           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
ubuntu@ubuntu:~$ 


What I am guessing is happening here: the installation program is unable to comprehend that the 2 160GB drives are in a RAID 0 array. It then installs the OS on drive a. When the comp tries to boot, since the controller is telling the comp that it is in a raid, but there is no information on disk b, the boot fails.

So how do I join disk a with disk b and then install the OS?

To answer your previous question: i believe the RAID is a hardware raid. I am only somewhat literate in these things, but i know that when I boot the system, along with my normal boot messages, I get a RAID boot message, and can configure the RAID array before XP was even loaded.

Thank you for any assistance.

---

### Post by vtel57 on 2007-05-25
OK, yes... that is a hardware RAID. Good! Unfortunately, I have no expertise in loading Linux onto a RAID array. My RAID (1) array is software RAID and only contains my rarely used Win XP Pro installation. My Linux drive is IDE. 

Your theory is probably accurate, though. Your fdisk is showing the Ubuntu installed on the sda drive (SATA master), but your sdb (SATA slave) drive is empty. I would do a search here on this forum and on Google for installing Linux on hardware RAID arrays and see what you come up with. In the meantime, maybe someone will pop in here to assist you with this.

Best of luck!

---

### Post by ksd123 on 2007-05-25
Thank you for your assistance.

---

### Post by dstew on 2007-05-25
This might help: [Fake Raid How-To]("https://help.ubuntu.com/community/FakeRaidHowto"). It seems that, if you want to install to a RAID, you need to install the software that handles the disks as a RAID onto the Live CD file system before you do the installation. Yes, you can install programs onto the Live CD file system, but they disappear when you shut down.

---

### Post by ksd123 on 2007-05-25
Yup, I looked at that and started to work on it. Despite what appears to be excellent instructions, I was totally unable to even down load dmraid.

Here is the problem. Ubuntu is supposed to be simple and user friendly and available for a wide variety of platforms. I am just a simple user. I use a computer for work and playing video games. Now I have had a computer for a long time and I might have a little more knowledge than most people, but not much. It seems like even the well written instructions from the FakeRaid How-to very quickly break down into technical speak, and you need to be somewhat versed in Linux to proceed. I don't even know what a kernel is.

That being said, the people at Ubuntu need to realize that if they want to promote this operating system to the masses (which they are through their partnership with Dell), they need to make it usable for people like me, who think kernels are what I pop in the microwave before a movie. Usable means that it should do something simple like recognize a simple raid array on install.

I find it hard to believe that an O/S that is designed to work in business environments does not have this support out of the box.

So I appreciate the help from everyone, but I will now be reinstalling Windows <sigh>. Sucks because I really wanted to see something good and new because I hate windows, and couldn't even get it to boot. GG.

---

