---
title: "Grub Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Jay the Great on 2006-10-22
I have two different hard drives. One with XP pro and one with Ubuntu.

Ubuntu = Master
Windows XP = Slave

Now, the reason I think I'm having problems is that when I installed ubuntu, my Windows XP hard drive was not connected to the computer at all. Now, I'm trying to get ubuntu to recognize that I want to boot from my Windows XP hard drive sometimes. When I hit "escape" to bring the menu up and choose "Windows XP" I get the following error:

[B]Booting Microsoft Windows
root hd0,0
File system type is ext2fs, partition type 0x83
savedefault
make active
chainloader +1

Error 13
Invalid or unsupported executable format[/B]

---

### Post by catlett on 2006-10-22
You need to change the entry for windows. Open a terminal and enter ```
sudo gedit /boot/grub/menu.lst
``` Erase the entry you have for windows and replace it with this
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
As long as you have ubuntu as the master and XP as the slave drive, that will work. If you get an error then something is wrong and we'll have to start trouble shooting but if it is just the entry, that will fix it.

---

### Post by Jay the Great on 2006-10-22
That worked. Thanks a lot. \\:D/

---

### Post by catlett on 2006-10-22
> **Jay the Great said:**
> That worked. Thanks a lot. \\:D/

Anytime.;)

---

### Post by prophet11 on 2006-11-02
i got this error Computer displayed windows root\system32\hal.dll is missing or corrupt

can someone hook me up with that dll or tlel me how i can fix it?

---

### Post by moffa on 2006-11-03
Did you change anything in the windows boot.ini file?

---

### Post by prophet11 on 2006-11-03
no i just did that suggested and it happened

---

### Post by Herman on 2006-11-03
Have you used some disk partitioning software and told it to change the partition number of your Windows parition? (Or allowed it to do that).

If you did then you need to either copy and paste the partition back again to get the old partition number back, (usually partition number1 or /dev/hda1 for Windows), or else edit boot.ini with the changes.

---

### Post by prophet11 on 2006-11-04
i cahnged r disk to 1 it was 0 but it still does it ether way

i need to figure out why it says the hal.dll is missing

---

### Post by Herman on 2006-11-04
Can you post a copy of 'sudo fdisk -lu' and if your Windows partition is /dev/hda1, (presuming it's mounted), a copy of 'cat /media/hda1/boot.ini' please? 
```
sudo fdisk -lu
``````
cat /media/hda1/boot.ini
```

---

### Post by Herman on 2006-11-04
For example, here is my boot.ini file,
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR=Red]**partition(1)**[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR=Red]**partition(1)**[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
```See how it has 'partition(1)' in both of the lines after the word 'partition'? :D

That corresponds with my hard disks partitioning arrangement. As you can see from my fdisk output, (below), Windows really is in partition number 1 in my computer.
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]**/dev/hda1   *          63    24579449    12289693+   c  W95 FAT32 (LBA)**[/COLOR]
/dev/hda2        24579450    96502454    35961502+  83  Linux
/dev/hda3        96502455   156296384    29896965    5  Extended
/dev/hda5        96502518    98896139     1196811   82  Linux swap / Solaris
/dev/hda6        98896203   116455184     8779491   83  Linux
/dev/hda7       116455248   120760604     2152678+  83  Linux
/dev/hda8       120760668   156296384    17767858+  83  Linux

Disk /dev/hdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63     1124549      562243+   b  W95 FAT32
/dev/hdb2   *     1124550    35037764    16956607+  83  Linux
/dev/hdb3        56725515    58605119      939802+   5  Extended
/dev/hdb4        35037765    56725514    10843875   83  Linux
/dev/hdb5        56725578    58605119      939771   82  Linux swap / Solaris

Partition table entries are not in disk order
herman@testedgyeftbeta:~$ 

``` Now, if I were to copy and paste my Windows partition with partition editing software, or if my Windows partition number was somehow changed in some other way, I would need to edit my boot.ini with the new partition numbers in those places, or it will say it can't find hal.dll

hal stands for hardware abstraction layer.

I don't really know much more about Windows than that, but I hope that will be enough to get you booting. You would get better Windows help in a Windows forum. :D

Regards, Herman :D

---

### Post by lsblakk on 2006-11-05
Hello, I also followed the instructions earlier in this thread.

Background:

Installed Ubuntu 6.10 where my former gentoo partition was on a dual boot laptop with XP Pro...everything was working fine, except I had messed up assigning enough harddrive space.  So I tried to work with gparted within the Ubuntu desktop but got confused and cancelled midway - this is when I rebooted and got the Grub Error 13 and came to this forum.

So I did the gedit on the menu.lst and windows still wouln't boot...something about missing a NMTSF (totally making that acronym up) and so I re-installed Ubuntu 6.10

In the re-install, I noticed that one of the small NTFS drive partitions (7GB) was flagged as boot and I remembered that the Windows partition (45gb) had originally been the one flagged as boot, so in the re-install I changed the flags, reinstalled, everything looked good...

That's when I got the system32/hal.dll error on rebooting.

I tried the recovery console but it's not accepting my admin password - 

My windows section is in partition 2, and you can see here:

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect



that it is so.  

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    37897334    18948636    5  Extended
/dev/hda2   *    37897335   135797444    48950055    7  HPFS/NTFS
/dev/hda3       135797445   140343839     2273197+  82  Linux swap / Solaris
/dev/hda4       140343840   156296384     7976272+   7  HPFS/NTFS
/dev/hda5             126     8112824     4056349+  83  Linux
/dev/hda6         8112888    37897334    14892223+   b  W95 FAT32


is my fdisk file.

Also - I am only able to read the boot.ini file - I don't know how I would go about changing it if that needed to change since the recovery console won't accept my admin password.

I've downloaded the 6.06 version and I am wondering if doing a re-install with that version might change anything.

Please help if you can.  Thanks!

---

### Post by catlett on 2006-11-05
Just to clarify the first post response. The issue the OP had was Ubuntu was the master hard drive and XP was the slave hard drive. He could not boot XP.
The solution I gave was a change in an Ubuntu system file. Namely the menu.lst for the application grub which is in the boot folder.
All that does is change the entry for XP in the file /boot/grub/menu.lst. That is all it is. Just a change in value in an Ubuntu file. There is no reformatting, reinstalling or moving partitions. Just a correction in the file to compensate for a 'quirk' in the windows bootloader. Windows likes to be on the master drive. The entry change is making use of a 'mapping' feature in grub. By mapping the XP partition (hd1) through the master drive location (hd0), windows is tricked into thinking it is on the master drive and it will boot.
This file /boot/grub/menu.lst has nothinbg to do with window's system configuration. It has no effect on window's internal files. It just changes the way Ubuntu's grub sends the boot to window's bootloader.
Do not change any values in the boot.ini file. This is for the menu.lst in grub. Do not alter any partitions to give them a different value which may match the example. The example is for someone with Ubuntu on the first hard drive and windows on the second hard drive. 

To the last poster. You do not have 2 hard drives, you have multiple partitions on 1 hard drive. Your windows partition is /dev/hda2 which would be (hd0,1) in grub.

If I had to guess, it seems people are changing the boot.ini in windows and the bootloader cannot find the file it needs because the ini file is sending it to the wrong partition. If you changed your boot.ini file, change it back. Ubuntu has read, write ability for ntfs with the installation of ntfs-3g [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)  That will give you the ability to write to your windows partition from ubuntu (you can then change your boot.ini file from ubuntu IF that is the issue). Or try the recovery console in windows again.(This would be the better option because writing to windows from ubuntu should only be done as a last resort) You should try using your personal password to enter the console. In windows, most users have administrator priveleges. [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by lsblakk on 2006-11-05
Thanks for the reply.

I never changed my boot.ini file to my knowledge - unless something in the unbuntu install process does this - i never touched the windows partition.  

And on the password front...i only have 5 passwords in my life, none of them work on the recovery console.  

What do you think of trying to install version 6.06 instead?  I have to get back my windows unfortunately, my school life depends on it.

---

### Post by catlett on 2006-11-05
> **lsblakk said:**
> Thanks for the reply.

I never changed my boot.ini file to my knowledge - unless something in the unbuntu install process does this - i never touched the windows partition.  

And on the password front...i only have 5 passwords in my life, none of them work on the recovery console.  

What do you think of trying to install version 6.06 instead?  I have to get back my windows unfortunately, my school life depends on it.

I would try installing 6.06 Let it do it's thing. Just make sure it doesn't touch the windows partition. Grub should install with access to both operating systems. Install Ubuntu. If you can get into ubuntu but not XP, we can edit the grub file so you get into windows. As long as window's partition hasn't been formatted it is there and you can get it back. First run the 6.06 installer and see what happens.
Just remeber when installing, your windows is installed on /dev/hda2.
Do you know what is on /dev/hda4? That is formatted as ntfs as well.

When you install, to be safe only format hda3 and hda5. Make hda3 linux-swap and make hda5 root. Leave the rest as it is just to be safe. This way you are only reformatting the ext3 and the swap. They are definately ubuntu partitions.

---

### Post by prophet11 on 2006-11-05
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   228363974   114181956   83  Linux
/dev/hda2       228363975   234436544     3036285    5  Extended
/dev/hda5       228364038   234436544     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/hdc: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63    19518974     9759456    7  HPFS/NTFS


my boot ini i the same as yours but the cat command didnt wrk

---

### Post by lsblakk on 2006-11-05
> **catlett said:**
> I would try installing 6.06 Let it do it's thing. Just make sure it doesn't touch the windows partition. Grub should install with access to both operating systems. Install Ubuntu. If you can get into ubuntu but not XP, we can edit the grub file so you get into windows. As long as window's partition hasn't been formatted it is there and you can get it back. First run the 6.06 installer and see what happens.
Just remeber when installing, your windows is installed on /dev/hda2.
Do you know what is on /dev/hda4? That is formatted as ntfs as well.

When you install, to be safe only format hda3 and hda5. Make hda3 linux-swap and make hda5 root. Leave the rest as it is just to be safe. This way you are only reformatting the ext3 and the swap. They are definately ubuntu partitions.


Hello again - well, i installed the 6.06 and when i go into grub and select the windows, i'm still getting the system32/hal.dll error message.

my windows partition is definitely hda2 and nothing about that partition has been formatted or touched. does it seem strange that my boot.ini file has a /noexecute=optin / before the fastdetect?  i notice that no one else's boot.ini file mentions this... 

any suggestions?

---

### Post by catlett on 2006-11-06
Hi Isblakk,
Do you have an XP installation disk? Not a computer maker recovery disk like dell or gateway but a real xp install disk? If you do, it appears you can fix this with the recovery console. If you don't have an XP install disk, I suggest you put in the Ubuntu live cd and download an XP install iso, burn it to disk and boot to the recovery console. [http://www.torrentspy.com/torrent/899070/windows_xp_pro](http://www.torrentspy.com/torrent/899070/windows_xp_pro)
This is microsofts documentation on the recovery console. [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058) It is a new feature, well new to xp, that everyone who has xp is entitiled to.People who only get computer maker recovery disks loose out because it is only on the install disks. It is relativley easy to get into. Just boot to the cd and press r at the prompt. Then follow the prompts to enter into the console which is a command line.
This article has the commands for fixing the hal file [http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm) They list a couple of different methods, but this looks like the simplest method. At the command line, enter this 
```

Attrib -H -R -S C:\Boot.ini
DEL C:\Boot.ini
BootCfg /Rebuild
Fixboot
```

---

### Post by lsblakk on 2006-11-07
Hi - thanks for your help.  I just spent all day re-installing windows...sigh.  BUt anyway, after re-installing windows (without reformatting the disk so i didn't lose anything) I was able to re-install grub as well and now i have the ability to dual boot into both again.

phew!

that was a lot of extra work but i guess i learned a lot and did a little spring cleaning while i was at it.

thanks again.  i think i will wait until this semester is over before playing around with my set-up again.  too much at stake.

---

### Post by catlett on 2006-11-07
> **lsblakk said:**
> Hi - thanks for your help.  I just spent all day re-installing windows...sigh.  BUt anyway, after re-installing windows (without reformatting the disk so i didn't lose anything) I was able to re-install grub as well and now i have the ability to dual boot into both again.

phew!

that was a lot of extra work but i guess i learned a lot and did a little spring cleaning while i was at it.

thanks again.  i think i will wait until this semester is over before playing around with my set-up again.  too much at stake.

Not to sound like a nag, but always have a current backup. Not just because of dual booting but things do happen and backups are your 'safety net'. External hard drives are getting cheaper and cheaper. Save up and buy one, they are the best thing (outside of having a raid setup). This way you keep the external offline (so it can't get corrupted) and at the end of your day or the end of your session, back up any new data to it. I haven't searched but I think there are some free backup apps, actually I think my external came with one.
Enough of preaching, glad your up and rumming. Take care.

---

### Post by Herman on 2006-11-08
Hello, prophet11,
Here's a link about 'hall.dll missing or corrupt', it's quite a long thread though, and it looks like lots of things can cause that error message in WIndows. [http://www.nocrash.com/ncbbs/msgs/162.shtml](http://www.nocrash.com/ncbbs/msgs/162.shtml)

I do know that one way to reproduce the exact same error message is to deliberately mis-edit the partition numbers in my own boot.ini file, because to make sure I am testing that now, and I have up in my other monitor at the moment, (typing this on my laptop): > Windows could not start because the following file is missing 
or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file. I remember a while back when someone else reported how they repaired this error was caused by a mistake they made during partitioning which caused their Windows partition number to be changed. They fixed it by using some special software they found that can write to NTFS from Ubuntu, and edited boot.ini with the new partition numbers and that's how one user solved it. 
However, a better idea would be to boot your Windows installation with a Windows XP boot floppy disk, you can make one of those yourself. Here's the link, for Windows XP, [How To Create a Boot Disk for an NTFS or FAT Partition in Windows XP]("http://support.microsoft.com/kb/305595/EN-US/")
For Windows NT, 2000, [http://support.microsoft.com/kb/301680/en-us](http://support.microsoft.com/kb/301680/en-us)
Then edit boot.ini from within Windows itself, (presuming that is the problem).

I recommend Windows users make one of those boot disks, basically you need to carfully follow the instructions about how to format the floppy disk a specail way from Windows command line, then copy boot.ini, NTLDR, and NTDetect to the bootable foppy disk.   I have found these to be the most reliable way of all to boot Windows XP, I do a lot of experiments with bootloaders, and break my system on purpose quite often just to see how to fix it again. These boot floppies will boot Windows even with no MBR or bootsector, if boot.ini needs editing, or even if it is missing. You can edit the boot.ini on the floppy disk from Ubuntu if you need to, the floppy disk is FAT32 so it can be safely written to from Linux. 

However, as explained in the first link I provided in this post, it's a Windows problem and has nothing to do with Ubuntu, and lots of things can cause it. The best thing to do is ditch Windows and just use Ubuntu. :D
(I mean this in a freindly way). :D

Regards, Herman :D

---

### Post by rowdy15 on 2007-02-21
Hey guys,

I am a total and utter noob at ubuntu and linux,

I just installed ubuntu 6.10 yesterday, 

i have one hard drive and as such used the ubuntu 6.10 live cd to partition some space for installation of Ubuntu 6.10 without losing windows............during the installation process of ubuntu 6.10

.................Went fine.

i did a few things on ubuntu yesterday like try into install java etc (don't know if it worked or not)

but that's beside the point of my problem

i then tried booting up windows today from the start screen (which gives you what to choose to boot up)................  and it worked but said it had found new devices and needed to reboot.................once i did this, i then couldn't boot up windows after this point!!!!!

at the boot start screen when i try to boot windows it comes up with "Error 13 invalid or unsupported executable format"

I really need to be able to have both windows and Ubuntu on the same HDD

please help:(

i should also mention I am using my laptop...........just in case that means anything

---

### Post by x64Jimbo on 2007-05-10
Same problem as OP, but when trying to boot Ubuntu. Neither rescue mode nor normal mode work - both produce that error. I've never seen this before; can someone tell me what's going on?
I have all my stuff on one hard disk (the master) in my laptop. It's partitioned for a dual boot setup.

---

### Post by Herman on 2007-05-10
Any clues? fdisk output? bottom of menu.lst? background info, history? :)

Maybe try a file system check.  An easy way is to boot a [GParted -- LiveCD]("http://gparted.sourceforge.net/") and right-click on the partition and click 'check'.

---

### Post by jakedeg on 2007-10-21
> **catlett said:**
> You need to change the entry for windows. Open a terminal and enter ```
sudo gedit /boot/grub/menu.lst
``` Erase the entry you have for windows and replace it with this
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
As long as you have ubuntu as the master and XP as the slave drive, that will work. If you get an error then something is wrong and we'll have to start trouble shooting but if it is just the entry, that will fix it.


I'm hoping someone out there can help me with similar grub problem. I am dual-booting 7.10 and OSx. I have 2 physical drives. The first (primary) is one big partition which has 7.10 is installed on it and working great. The second has 2 partitions. Right now, OSx is installed on both partitions. I can make it boot from the first partition with no problem using

```
title     Mac OS x Partition 1
root     (hd1, 0)
savedefault
makeactive
chainloader     +1
```

When I try to load the installation on the second partition, though, I get an

```
Error 13: Invalid or unsupported executable format

Press any key to continue...
```

Any ideas what is wrong here? Do I need to use 'map' somehow?

Thanks so much,
Jake

---

### Post by Herman on 2007-10-22
Hello jakedeg,
I can only see one small mistake there, you have a whitespace (gap) between the 1, and 0 in the (hd1,0) ,
```
title     Mac OS x Partition 1
root    [COLOR=Red]** (hd1, 0)**[/COLOR]
savedefault
makeactive
chainloader     +1
```
Change to,
```
title     Mac OS x Partition 1
root     (hd1,0)
savedefault
makeactive
chainloader     +1
```
I don't know anything about Macs except that I don't know much about them.
I think the map commands are only needed for Windows, but you can try them.
I googled for some more information but it looks like there are a lot of different kinds of Mac setups.  Does your have a DOS type of MBR? 
I did see some web pages where I saw similar types of boot entries suggested, so it should be possible, for some Mac OSes at least.

Maybe someone else who know more about Macs can help you some more if that wasn't the problem.

Good luck with it,
Regards, Herman :)

---

### Post by ukripper on 2007-12-02
> **catlett said:**
> You need to change the entry for windows. Open a terminal and enter ```
sudo gedit /boot/grub/menu.lst
``` Erase the entry you have for windows and replace it with this
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
As long as you have ubuntu as the master and XP as the slave drive, that will work. If you get an error then something is wrong and we'll have to start trouble shooting but if it is just the entry, that will fix it.

Thanks alot mate, you saved me bigtime! After fixing grub from super disk i had that error 13 tried swapping and mapping nothing worked then saw your post. worked like charm now i had to change ubuntu to hd0,0 . 

Cheers
ukripper

---

### Post by asantainnasa on 2007-12-18
hi guys
i'm having a similar problem
i recently had a BSD on my windows
and after that i've been getting

```
Error 13: Invalid or unsupported executable format

Press any key to continue...

```

this is my entry for windows in my grub menu.lst

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,2)
savedefault
makeactive
chainloader     +1
```


my output for fdisk is
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   131074334    65537136    5  Extended
/dev/sda2   *   131074335   156248189    12586927+   7  HPFS/NTFS
/dev/sda5             126   128969819    64484847   83  Linux
/dev/sda6       128969883   131074334     1052226   82  Linux swap / Solaris

```

i'm trying to get some help before i reinstall my windows again
thanks for anything! =]

---

### Post by Herman on 2007-12-18
```
/dev/sda2   *   131074335   156248189    12586927+   7  HPFS/NTFS
```Your Windows Xp partition is /dev/sda2, that's equivalent to (hd0,1) in GRUB terms. 
Try replacing the (hd0,2) you have with (hd0,1) and see if that works or not.
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0[COLOR=Red]**,1**[/COLOR])
savedefault
makeactive
chainloader     +1
```Regards,Herman :)

---

### Post by asantainnasa on 2007-12-18
> **Herman said:**
> ```
/dev/sda2   *   131074335   156248189    12586927+   7  HPFS/NTFS
```Your Windows Xp partition is /dev/sda2, that's equivalent to (hd0,1) in GRUB terms. 
Try replacing the (hd0,2) you have with (hd0,1) and see if that works or not.
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0[COLOR=Red]**,1**[/COLOR])
savedefault
makeactive
chainloader     +1
```Regards,Herman :)


Thanks for you advice. I did what you suggested, but I am still getting the same message about "Invalid or unsupported executable format"
>.<
and my linux does not even detect the device when i try to manually mount it

---

### Post by Herman on 2007-12-18
Try experimenting with  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and try to see if you can boot with different partition numbers then or a different hard disk numbers.

If you have a Windows 'Installation' CD (not a 'Recovery Disk'), and you can get a  [Windows XP 'Recovery Console]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console"), try the FIXBOOT command in case there might be something wrong with the boot sector.

If it still won't boot, go to this website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"). Download the Windows XP boot CD-ROM from that site and try to boot with that. That CD will bypass the MBR and the boot sector and the Windows bootloader files as well. You should be able to boot with that for sure.

If you still can't boot, try running CHKDSK from [Windows XP 'Recovery Console]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console"), and see if that helps.

Those are about all the ideas I can think of right now, I hope one of those will work for you.
Regards, Herman :)

---

### Post by widowmaker03 on 2007-12-18
catlet,

Thanks.  I wish I had seen your response before I posted about my dual boot problem.  I followed you instructions and my problem is fixed.

---

### Post by yetkin on 2008-06-22
Sometimes GRUB doesn't warn you with "error 13" for Windows partition just a blank screen and holds.
but thank you
"map (hda1) (hd0)"
"map (hd0) (hd1)"
trick works! i did it for Solaris which i installed on a slave 80Gb
and used its GRUB to boot my master's linux and Windows partitions. Just it will be a problem when i upgrade my linux kernel ( : i will have to modify menu.lst file of Solaris' /boot

thank you for "map" trick.

---

