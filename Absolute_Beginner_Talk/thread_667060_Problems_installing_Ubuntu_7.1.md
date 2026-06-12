---
title: "Problems installing Ubuntu 7.1"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by dnguyen1022 on 2008-01-14
Hey I'm trying to install Ubuntu 7.1 on my external hard drive from my laptp but there is a problem.  I disabled my main hard drive in the BIOS by the way, so it doesnt even run/boot.  I was able to boot the disc and choose it to install, but it gives me an error about "something unable to allocate resources"..flickers and then turns black.  I leave it there for 5 minutes and then i finally get some results.  It says it has to run my thing in low graphics mode, and if I wanted to do otherwise I have to manually configure it..So I press the configure button, and manually configure my monitor size.  I press okay and it just goes black for a bit and then runs some sort of script.  I am then able to type anything I want.  I don't know what to type as I was expecting some sort of testing of Ubuntu before I install it?  I decided to reboot and try again..this time I did not configure the monitor I just left it as it is..and this I end up at some screen that tells me what a sudo command is, and some other commands and again I have the ability to type something.  If im not wrong i'm suppose to end up at some screen that allows me to test out ubuntu before installing it.  I only end up with some dos like screens that allow me to type in commands.  My laptop is a CompalIFL90/Sager2090 running on a nvidia 8600mgt.  I am also using the 64 bit version of the desktop ubuntu.  I was able to find a site on people who have installed Ubuntu using the alternate CD, but not the regular one I have.  Is there any way to fix my problem, or do I have to use the alternate CD?  Are there guides to the alternate cd by the way?  I only see ones for the regular desktop versions, or are they both the same?

---

### Post by -grubby on 2008-01-14
There aren't really any mature drivers for the 8600 yet. You will have to use the alternative CD. Here's a [link]("http://www.robdian.co.uk/content/view/56/27/") to a guide on it

---

### Post by dnguyen1022 on 2008-01-14
mm I have an internet connection but will I be able to access this site from the alternate CD? Also whats the difference between the alternate cd and the regular desktop one.

---

### Post by dnguyen1022 on 2008-01-14
bump due to bein on like the 7th page lol

---

### Post by dstew on 2008-01-14
The Alternate Install CD installs the same Ubuntu system using a text-based installer. It does not have the ability to run the temporary Ubuntu sysytem that people try out before installing. If you know you want to install, use the Alternate Install CD. [Here]("http://users.bigpond.net.au/hermanzone/") is a guide.

---

### Post by dnguyen1022 on 2008-01-15
ooo thanks..by the way even though I am on a 64 bit system can I just install 32 bit ubuntu as I am planning to run eclipse and I know that there are some errors with 64 bit OS and eclipse?  i know windows xp works but not sure about linux...im a noob.

---

### Post by dstew on 2008-01-15
The 32 bit Ubuntu will work fine on a 64 bit system.

---

### Post by ByteJuggler on 2008-01-15
> **dnguyen1022 said:**
> ooo thanks..by the way even though I am on a 64 bit system can I just install 32 bit ubuntu as I am planning to run eclipse and I know that there are some errors with 64 bit OS and eclipse?  i know windows xp works but not sure about linux...im a noob.

The biggest reason for installing the 64bit edition is to support 4GB and greater memory sizes.  If you currently have less than about 3.2GB RAM then there's not a big reason to install the 64-bit version and the 32-bit edition will work just as well.  To clarify: The 32 bit edition can only access up to 4GB or RAM, and can only usefully use/supply about 3.2GB of that to applications.  The 64-bit edition doesn't have this limitation.  

(Aside: There are other minor enhancements when running 64-bit but for the most part they are invisible except when running specifically 64-bit tuned software making use of these features.)

---

### Post by dnguyen1022 on 2008-01-17
sooo i booted up ubuntu alternate, then at the partition screen i got lost.
I'm trying to install ubuntu on a whole new external hard drive from my laptop (disconnected the main one), but I come across the file formats and stuff.  I know Ubuntu uses the ext3 system.  I'm just not sure about the mount points.  What im trying to do is use 40gb for ubuntu 1 gb of swap, and the rest for whatever stuff I want to store in it from windows as ntfs by the way or fat32 so i can reformat it back to nfts.  Can someone lead me in the right direction when doing these mount points?  also the bootable flags.  Do I turn on the bootable flag for the one that I want ubuntu to be on?  I followed the above links to help me with the alternate disc but the guide he writes has wayy to many partitions.

---

### Post by ByteJuggler on 2008-01-17
Make a 1GB partition, specify mount point "swap" for it

Make a 40GB partition, specify mount point "/"  for it (pronounced as "root" as "/" is the root folder)  Mark it as active/bootable. 

That's it really.  

You can leave making the shared partition until later.  If you want to format it NTFS , then make it and format it from Windows.  You can then set up its mounting in Linux afterwards.

---

### Post by dnguyen1022 on 2008-01-19
ok i was able to install ubuntu on a external hard drive by removing my hard drive..it is running great except for 3 things im concerned about...
lets start with the minor problems first..

1. my time is wrong on windows vista after i boot up from ubuntu, then restart and go to vista my time is off by many hours.  i only thought this affected vista..i was wrong..i just booted up ubuntu today and it had the wrong time and the wrong year month so on.

2. I partitioned about 50gb for ubuntu and 1gb for swap. i left the rest as free space. how do i make it so i can format that free space in windows..also how do i make my windows recognize the format the linux partition is in, and vice versa?

3. how do I change the grub menu now so that i can choose whether i want to boot up from windows or linux when my hard drive is plugged in?

---

### Post by ByteJuggler on 2008-01-19
> **dnguyen1022 said:**
> ok i was able to install ubuntu on a external hard drive by removing my hard drive..it is running great except for 3 things im concerned about...
lets start with the minor problems first..

1. my time is wrong on windows vista after i boot up from ubuntu, then restart and go to vista my time is off by many hours.  i only thought this affected vista..i was wrong..i just booted up ubuntu today and it had the wrong time and the wrong year month so on.


I'm not sure why your time is wrong etc.  Perhaps this thread is relevant:  [http://ubuntuforums.org/showthread.php?t=580160](http://ubuntuforums.org/showthread.php?t=580160)

Let me know if it helps or not.

> **dnguyen1022 said:**
> 
2. I partitioned about 50gb for ubuntu and 1gb for swap. i left the rest as free space. how do i make it so i can format that free space in windows..also how do i make my windows recognize the format the linux partition is in, and vice versa?


Boot up Windows, go into disk management on Vista (that is, "Start"->"Control Panel"->"Classic view" if required->"Administrative tools"->"computer management"->"disk management", in the drive display, find the the unallocated space on the hard drive (the black bit saying "Unallocated") and right click on it, click "New simple volume", follow the wizard, click "Assign Drive letter" when you get to that option, on the next page in "Volume Label" type in "SharedData", Click "Next, Click "Finish".  Windows should format your partition and you can then use it.  When next you boot into Linux, you should be able to also see the SharedDate partition in "Places" at least, if not as a shortcut on your desktop.  

That's roughly it.

> **dnguyen1022 said:**
> 
3. how do I change the grub menu now so that i can choose whether i want to boot up from windows or linux when my hard drive is plugged in?

OK to help you with that, I need some info.  Please boot Linux, then at the desktop press alt-f2 and copy/past or type the following command into the box shown, and press enter afterwards:

```
sudo fdisk -lu > /tmp/fdisk.txt; gedit /tmp/fdisk.txt
```

A text editor with the output of the "fdisk -lu" command will be displayed.  Please post it here by copying and pasting it here.  Then I'll try to tell you how to change your menu.lst to boot Windows even when the external disk is connected.

---

### Post by dnguyen1022 on 2008-01-23
mmm do I have to name the partition as SharedData?

---

### Post by dnguyen1022 on 2008-01-23
damn...I didnt name it as SharedData and when I try to boot linux up again from the external hard drive i get an error 17.  I searched this up and only found stuff on the live boot cd. is there a way from the alternative disk?  I also deleted the newly formatted part of the drive.  I'm still getting error 17.

EDIT: I also just tried the super grub disk...i got a little bit farther as now it detects my kernels but when i press enter on one of them it gives me error 17: can not mount partition...whereas before it just says error 17.

---

### Post by dnguyen1022 on 2008-01-24
bumpp

---

### Post by ByteJuggler on 2008-01-24
Boot your LiveCD, and perform the last command I gave you (press alt-f2 and post the output of the command shown):

```
sudo fdisk -lu > /tmp/fdisk.txt; gedit /tmp/fdisk.txt
```

It sounds like you might've deleted a partition needed for booting or your partition is in a different place to where it was when you installed.   (Error 17 = failed to mount selected partition )  This can be due to drive ordering in the bios changing for example.

For now, please post the output of the above command.

---

### Post by dnguyen1022 on 2008-01-26
..problem is i cant boot from the livecd because ubuntu does not support my gcard, so I had to do it with the alternative disc.

---

### Post by ByteJuggler on 2008-01-26
> **dnguyen1022 said:**
> ..problem is i cant boot from the livecd because ubuntu does not support my gcard, so I had to do it with the alternative disc.

And I presume "Safe graphics mode" on the normal CD also doesn't work?  (Just checking.)

---

### Post by dnguyen1022 on 2008-01-26
wow never knew safe graphics would work here...


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9460a08b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234438655   117218304    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    97659134    48829536   83  Linux
/dev/sdb2       486432135   488392064      979965    5  Extended
/dev/sdb5       486448200   488392064      971932+  82  Linux swap / Solaris

---

### Post by dnguyen1022 on 2008-01-27
bumpity bump

---

### Post by dnguyen1022 on 2008-01-27
bump yet again for being like on the 10th page

---

### Post by ByteJuggler on 2008-01-28
> **dnguyen1022 said:**
> wow never knew safe graphics would work here...


So can you actually boot to a desktop then with the LiveCD using the safe graphics option?

If not, things become slightly complicated, I'm not [yet] familiar with the alternate install cd and how you would work from there.  But basically, you have to delete your previous partitions, then re-install again onto the blank space left by them.

Edit:  I would suggest you boot back into Windows Vista and use it to completely wipe your external disk again, so you can start over.  Go into "Control Panel" (classic mode) -> "Admin tools" ->"Computer Management"->"Disk management" and delete the partitions on your exernal disk so all the space show as unallocated.  

Check if you can boot cleanly again and if not, then you may also want to boot from your Vista CD, into a command prompt, and do:
> bootrec /fixmbr
bootrec /fixboot

After that you should be able to boot cleanly with no GRUB errors and can start again installing Linux.  If Safe Graphics mode works, you can try that when installing.

---

### Post by dnguyen1022 on 2008-01-28
okay so i decided to reinstall my linux as it was sort of urgently needed...now i want to know how to be able to add windows vista to the grub menu..

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9460a08b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234438655   117218304    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    97659134    48829536   83  Linux
/dev/sdb2        97660928   486430719   194384896    7  HPFS/NTFS
/dev/sdb3       486432135   488392064      979965    5  Extended
/dev/sdb5       486432198   488392064      979933+  82  Linux swap / Solaris

---

### Post by dnguyen1022 on 2008-02-01
bumppp

---

### Post by dnguyen1022 on 2008-02-03
bumpp

---

### Post by dnguyen1022 on 2008-02-08
bumpity bump

---

