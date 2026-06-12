---
title: "cant get dual booting to work (ubuntu winXP)"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by lumarh on 2007-03-12
I have already installed windows and set up drivers etc on the smaller 8gig slave, 
then i put ubuntu on the main 80gig master, but grub doesnt see windows. 

ive tried a few entries on the grub list, whatever its called something.list
including mapping hd0 hd1 and hd1 hd0.

could i get a hand with it? im willing to start from scratch to help work through it. any suggestions appreciated, thanks

---

### Post by xyz on 2007-03-12
You may want to check out this howto and see if you did everything right.
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by lumarh on 2007-03-12
ive looked over it and followed its instructions, but i cant find anything in the guide on an error im getting.
i get hit with "NTLDR is missing" when i try to load windows..
does this mean i have to reinstall windows?

and if i do reinstall windows...is it possible to get grub back as windows seems to take over the boot record and not give me grub at startup any more...or is that just a matter of booting from the right hardrive via BIOS

---

### Post by louieb on 2007-03-12
I have close to the same setup. This is out my /boot/grub/menu.lst. It works for me.
```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot


```If that does not work please post the display from Applications>Accessories>Terminal ```
sudo fdisk -l
``` thats an l as in little.
Just saw your ntldr msg you may need to reinstall XP but let try some other things first.

---

### Post by stig on 2007-03-12
> **lumarh said:**
> ...could i get a hand with it? im willing to start from scratch to help work through it. any suggestions appreciated, thanks


This link might give extra info too, and it has other pages concerned with partitioning. It is a good source of Ubuntu info.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by J11Gyro on 2007-03-12
The way I have mine set-up is Windblows XP on master and Ubuntu on slave. works great. Windows has to be installed first and someone here told me to make sure to put ubuntu on slave. Hope this helps

---

### Post by dstew on 2007-03-12
"NTLDR is missing" is an error message from the Windows boot system. It probably means that you overwrote the Windows boot loader when you installed Grub. This can happen if you tell Grub to install in hd0,0 instead of hd0.

To repair the Windows boot loader, use the  Windows recovery console and the command fixboot.

---

### Post by daf1 on 2007-03-12
Hi 
    Ive been reading through these threads and thought I might add my limited experience, I,m new to linux and my mate and myself have installed ubuntu on three different computers, two we have duel booted with Xp, one we set up with xp/master and ubuntu/slave
and another the opposite,used the same code as LOUIEB in the /boot/grub/menu.lst and both worked ok. Hit ESC on boot and choose XP or Ubuntu,(I'm now going to read on to try and get my DVD to work in ubuntu)
                                       DAF1

---

### Post by lumarh on 2007-03-12
ok i will do all of this after uni today as i dont have time at the moment
thanks all.

dstew: if i do a fixboot will that in turn overwrite grub?

---

### Post by dstew on 2007-03-12
Fixboot will overwrite whatever is in the boot sector of a partition. Grub installs stage 1 into the MBR of a disk. The MBR is not part of any partition. It contains the stage 1 booter and the partition table for the disk.

Grub stage 1.5 goes into the boot sector of the partition you specify to grub as root. Usually this is your linux disk. However, if by mistake you put a linux stage 1.5 booter into the boot sector of your Windows partition, then Windows can't boot itself. It needs its own booter. Fixboot restores the Windows booter to its boot sector, but does not change the MBR.

If you want to get grub out of the MBR, you can use the Windows recovery console, and enter the command fixmbr.

---

### Post by lumarh on 2007-03-14
i ran fixboot in the recovery console, it told me the target petition was drive E and then proceeded to fix it.

i still get NTLDR is missing when i try to boot windows from grub though...perhaps i 'fixed' the wrong 'boot' ? how can i tell which petition to fix the boot sector of? i have windows on a seperate slaved HD

if i end up reinstalling winXP, that in turn gets rid of grub from my experience. I dont want to do that unless for certain i can get grub back up and come back into my current install of ubuntu

---

### Post by DaveyG on 2007-03-14
Have you tried putting Xp set to master on primary, then Ubuntu Master on secondary? then put the cd drives (if your using any) on slave(s)... then use Grub to choose wich os you wanna boot from.

Davey

---

### Post by lumarh on 2007-03-14
what will that do? im trying to use grub to choose my OS now but the boot record for windows is kaput....

---

### Post by dstew on 2007-03-14
I am no Windows guru, but I believe that the Windows recovery console has tools to let you see your partitions with Windows names. I think the map command is the one to use. Then you can see what devices go with what partitions, and make sure that you direct fixboot to the correct one. Here is a good web site that talks about the recovery console and its various programs:

[http://www.computerhope.com/jargon/r/recocons.htm](http://www.computerhope.com/jargon/r/recocons.htm)

---

### Post by dannyboy79 on 2007-03-14
> **dstew said:**
> I am no Windows guru, but I believe that the Windows recovery console has tools to let you see your partitions with Windows names. I think the map command is the one to use. Then you can see what devices go with what partitions, and make sure that you direct fixboot to the correct one. Here is a good web site that talks about the recovery console and its various programs:

[http://www.computerhope.com/jargon/r/recocons.htm](http://www.computerhope.com/jargon/r/recocons.htm)
per here: [http://support.microsoft.com/kb/q307654/](http://support.microsoft.com/kb/q307654/)

**Fixboot** writes a new startup sector on the system partition. 
which I don't believe was your problem!

**Fixmbr** repairs the startup partition's master boot code. The variable device is an optional name that specifies the device that requires a new Master Boot Record. Omit this variable when the target is the startup device. 
you didn't need to run fixboot, you needed to run fixmbr. you probably accidentally overwrote your windows mbr so you need to make it like it was after your windows install. windows loads the ntldr within the mbr of the drive loaded on. just boot to the recovery console and use the fixmbr option and you'll be set. also, you didn't delete your boot.ini or ntdetect.com file from your c drive did you? those missing will also cause issues but since it specifically stating the ntldr is missing than it's most likely what I said. 

also, this is important, you only need to use the grub map option, when you your windows drive is not your first drive, this is because windows can't boot to a non-first drive. at least according to gnu grub's manual. so please let me know what the exact order of your boot sequence is and what position your hard drives are in, also, post your menu.lst, also post your device.map file, also post your fdisk -l if you don't get it even after you do the fixmbr. good luck.

---

### Post by Matt1632 on 2007-03-14
How does one access the recovery console in windows?

---

### Post by dannyboy79 on 2007-03-14
no, you boot the winxp cd, then chose to run the recovery console. FYI, you could have easily found this out in gogle instead of waiting for some1 to answer. gogle will almost always have all of the answers to every one of your questions that you can ever dream of.

not to mention it stated this, "If you cannot start your computer, you can run the Recovery Console from the Microsoft Windows XP startup disks or the Windows XP CD-ROM" right inside the link I provided for actually using the recovery console.

---

### Post by dstew on 2007-03-14
The error message you are getting comes from the Windows boot loader, not from grub. It means that the Windows boot process started normally, but the boot loader could not find the hidden system file ntldr in the root directory of the partition that the boot loader was directed to. This can be caused by two things. One, the boot loader has been misdirected. This is likely to be your problem. Two, the boot loader is looking at the correct partition, but the ntldr file has been corrupted or erased. This is not likely to be the problem.

I do not know exactly how the Windows boot loader gets its directions, but my guess is that when it is installed by fixboot, it assumes that it is being placed into the first sector of the partition that contains the NT file system, and the ntldr file. After it loads, it looks into the root directory of the NTFS on that drive for ntldr. So, if you have the Windows boot loader on the wrong partition, that could cause the error.

For all the gory details of the Windows XP boot loading system,see:

[http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c28621675.mspx](http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c28621675.mspx)

---

### Post by Gauvenator on 2007-03-16
Will fixmbr cause any problems with Ubuntu starting?  I'm wondering because I have a similar problem.  I just installed Ubuntu today on an HP with XP and now XP won't start.  When I try to start XP the screen goes black and the some words (I don't remember them exactly) about "starting..." and it just sits there for a long time.  

I'm wondering if the Ubuntu install messed up XP's master boot record?

There are no error messages.

Thankyou for any help.

---

### Post by dannyboy79 on 2007-03-16
well, ubuntu install only would have messed up windows mbr IF you installed grub ot it's hard drive. what is your hard drive setup (ie which drive boots first, do you ahve more than 1 drive, did you install ubuntu on the second drive etc etc) do you remember what you picked when you installed grub? was it hd0 or hd1? why are you not booting windows from grub? or are you saying that's what happens after you pick windows from grub menu? if that's the case than you need to make sure that your boot.ini files and wahtnot are still in tact BUT ubuntu wouldn't have done anything to them UNLESS you chose to format your windows hard drive than, yeah, you messed up here. you just chose to reformat your windows hard drive if that's the case. did you chose for the installer to use it's auto option and make windows xp smaller and use the rest for ubuntu?

---

### Post by Herman on 2007-03-17
Hello,
There is no such thing as an 'XP's master boot record' :)

Windows doesn't have a Master Boot Record, it only has a boot sector. 

All hard disks have a Master Boot Record, but it isn't owned by any operating system. It isn't part of any operating system's file system. 

Gauvenator, 
I (or anyone), may be able to help you if you can supply more information, please? :)
It would be important to know more about this black screen when you try to boot Windows, especially whatever the error message is.
Also, from Ubuntu, if you can do 'sudo fdisk -lu' in a terminal and post the output here please? ```
sudo fdisk -lu
``` And also a copy of the bottom part of /boot/grub/menu.lst will probably be important, you get that with the following command, ```
sudo gedit /boot/grub/menu.lst
``` Thanks, there are always people here that will help, but we do need this important information before we can do anything.

Fixmbr will cause a lot of trouble with Ubuntu starting, I don't think it will help to do taht yet at this stage, we can probably fix this by a simple edit in your menu.lst file. if you do FIXMBR, it will just make it harder to access your grub files, you will probably be able to boot Windows, but you'll lose the boot of Ubuntu, so you'll be no further ahead.
A [Super Grub Disk]("http://supergrub.forjamari.linex.org/")__ will easily boot your Windows for the time being until we get your problem sorted out. :)
.........

[lumarh]("http://ubuntuforums.org/member.php?u=253830"), 
Your error message 'NTLDR is missing' when trying to load Windows is probably not true at all. 
I'll bet you will be able to check and see that NTLDR is actually still there by taking a look at this link **            [A Birds's eye view of Windows XP ]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")**[(showing the bootloaderfiles)]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP") by mounting your own Windows file system (if it isn't already automatically mounted), and you will see your boot.ini file. Please open it and check if it is correct for your current disk and partition numbers. If you are not sure, you could copy it and post it here, please and I'll take a look for you. :)
Neither Grub nor Ubuntu will not write to any part of your Windows filesystem at all unless you force them to do so yourself.

Further down in that link you will find another link about [How to create your own boot disk for Windows XP]("http://support.microsoft.com/kb/305595/EN-US/")
 You should be able to boot your Windows XP with one of those. These are much more than just your ordinary Windows boot disks. These have their own copy of NTLDR, NTdetect.com and boot.ini on the floppy disk. These will bypass most of your common Windows booting problems.
Since the floppy disk is FAT32, it is simple to edit the boot.ini file on the floppy disk from Ubuntu if that's all that is needed to get your Windows to boot (I think quite likely this will turn out to be your problem).
You must pay particular attention to how the link's instructions say you must format the floppy disk. I have tried other ways and only that way worked for me.
That should get your Windows booting for you for now. :)

If you could post your output from 'sudo fdisk -lu' in a terminal and post the output here too it would be good, please? ```
sudo fdisk -lu
```

Regards, Herman :)

---

### Post by Gauvenator on 2007-03-17
I have one hardrive that I partitioned for Linux.  I resized the windows partition and used it's leftover space for linux and its swap.  It doesn't boot windows after I choose it from the grub menu.  It basically freezes the computer, with no error codes/messages.


sudo fdisk -lu:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   521710874   260855406    7  HPFS/NTFS
/dev/sda2       568315440   586066319     8875440    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       521710875   563929694    21109410   83  Linux
/dev/sda4       563929695   568315439     2192872+  82  Linux swap / Solaris

Partition table entries are not in disk order

This is for the second code (I hope this is what you wanted):

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Gauvenator on 2007-03-17
The Fat32 is the recovery partition for windows, and the NTFS is windows.  Also, the recovery partition will still boot, just not Windows XP Media Center Edition

---

### Post by Gauvenator on 2007-03-17
Here is the contents of my boot.ini

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

Please let me know if it's not set up properly.

---

### Post by dstew on 2007-03-17
I am a bit puzzled. Does your grub boot menu include an entry for the linux system? If not, you might have set up your grub incorrectly.

---

### Post by Gauvenator on 2007-03-17
It has a Linux system entry.

---

### Post by dstew on 2007-03-17
Could you post it please? Also, post the contents of the file /boot/grub/device.map

---

### Post by Gauvenator on 2007-03-17
Boot Grub Device Map Contents:

(hd0)	/dev/sda



I will soon post Grub entry for Linux system.

---

### Post by Gauvenator on 2007-03-17
Here are all of the Grub choices:

Ubuntu, kernel 2.6.17-11-generic
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Windows XP Media Center Edition
Windows NT/2000/XP


The last entry is not an operating system (it's some sort of recovery thing that came with the computer), but it does boot.  Windows XP Media Center Edition is the one that will not boot.

---

### Post by dstew on 2007-03-17
I meant the contents of your /boot/grub/menu.lst file that have the linux boot items, but its OK, I think you are set up properly. For some reason, your Windows partition does not boot, even though grub seems to be set up correctly. Are there, in fact, no error messages at all after you select the Windows XP Media Center Edition menu item? It might be that the Windows boot sector is damaged.

---

### Post by Gauvenator on 2007-03-17
How do you fix the windows boot sector without messing up grub?
Should I use fixboot in the recovery console for windows, or will that mess up Ubuntu?

---

### Post by dstew on 2007-03-17
See Herman's post above about making an XP recovery disk, if you can. I think you can make one from the recovery console.

No, fixboot will not mess up grub unless you direct fixboot to write to the linux system partition. Doing fixboot on the Windows XP partition should cause no harm.

---

### Post by Gauvenator on 2007-03-17
so, because I have windows on C:, then I enter in the recovery console:

fixboot C:

Right?  That shouldn't harm linux, will it?  Also, does linux even give its drives letter names?

Also, how do you shut down from the recovery console?

---

### Post by Herman on 2007-03-17
Hello Gauvenator
Here is the best link I know of about how to use Windows [recovery console.]("http://www.kellys-korner-xp.com/win_xp_rec.htm")
I'm sorry but I can't help you with it myself, I have never used one.
Running fixboot on the Windows XP partition will cause no harm.

Here is my analysis of your fdisk output, I cannot see too much wrong except for the last partition not finishing on a cylinder boundary.
```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes

Device___Boot_______Start________End_______Blocks_______Id_______System
/dev/sda1___*__________63__521710874____260855406_________7_____HPFS/NTFS___Windows XP Media Center Edition_267.12 GB
/dev/sda3_______521710875__563929694______21109410_______83_____Linux________________________________________21.62 GB
/dev/sda4_______563929695__568315439_______2192872+______82_____Linux swap / Solaris__________________________2.25 GB
/dev/sda2_______568315440__586066319______8875440_____c W95_____FAT32 (LBA)_Windows NT/2000/XP________________9.1  GB
_________Partition 2 does not end on cylinder boundary.
``` Your other files look okay to me.
I cannot see exactly what the problem could be so far, so I hope the boot sector repair will help.
If not then yes, as dstew suggested, try making the [Windows XP boot floppy]("http://support.microsoft.com/kb/305595/EN-US/")
it should boot your Windows without any problem at all.

dstew, that's a brilliant idea to try formatting the floppy disk while in Windows recovery console. I hadn't thought of that. Good tip!  I do know that once the floppy is formatted in Windows it is simple to copy the needed files from the mounted partition with Ubuntu if necessary and write them to the floppy disk. Possibly that's easier to do with the recovery console as well. 

Like I said already, a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") should easily boot your Windows too, and it might be interesting to see if it will or not because that could be a clue.

Maybe if you can just get Windows to boot up and then try running a few maintenance utilities like scandisk and defrag it will clear the problem up. I'm serious, and if you cannot get Windows to boot it might be a good idea to use a [GParted LiveCD]("http://gparted.sourceforge.net/") and right-click on the partition and click 'check', then click 'apply' and then confirm it again on the confirmation screen. It's probably a good idea to try the simplest things first.

Regards, Herman :)

---

### Post by dstew on 2007-03-17
Yes, fixboot C:

Linux does not use letters for partition names. In Windows, a drive or a partition can be a letter. In Linux, a hard drive is hda or sda, and a partition is a drive name and a letter. like hda1 for the first partition on disk hda.

To quit the recovery console, type exit.

---

### Post by Gauvenator on 2007-03-17
I tried to use the Super Grub Disk and it did not work.  It did something similiar to what has been happening:  it just sits there with a blinking cursor after some words  (they were different in Super Grub, but no error message).  

Does the "..not end on a circular boundary."  mean something is really messed up with that partition?  Also, is partition 2 also sda2?

---

### Post by Gauvenator on 2007-03-17
I don't have a floppy drive, so I can't do the bootable floppy.

---

### Post by Herman on 2007-03-18
```
 [boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW  S

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windo  ws XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```I do see three mistakes in your boot.ini file, but I don't know if they are important or not. 
There is a gap between the 'W' and 'S' at the end of 'WINDOW S' in the third line.
There is a gap between the 'o' and the 'w' in the word 'windo ws' in the fifth line. ( don't think that would matter).
The boot.ini file you posted has all the lines spaced out. I don't think it will work that way, is that really what the file looks like or did you just post it like that for clarity?


```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```

---

### Post by Herman on 2007-03-18
Here is a Web page I found about how to make one of those floppy disks [Click Here]("http://tinyempire.com/notes/ntldrismissing.htm"), and it also has a link for '[What if the computer doesn't have a floppy drive?]("http://tinyempire.com/notes/ntldrismissing.htm#What_if_the_computer_doesn%27t_have_a_floppy_drive?")' I think you should be able to make a CD or a USB boot device.

Also, don't forget if you can't boot it, a filesystem check with a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") might be all you need.

Regards, Herman   :)

---

### Post by Gauvenator on 2007-03-18
My boot.ini doesn't really look like that.  It just copy and pasted funny.
I'm going to try the GParted LiveCD next.  If it finds an error in the file system, can it fix it?

---

### Post by Herman on 2007-03-18
>  I'm going to try the GParted LiveCD next.  If it finds an error in the file system, can it fix it? I think it will be able to fix it okay, there is a very good chance it can. But you should make a backup of your data first, especially valuable data. I guess you would already have done that, I'm just reminding you.
I use GParted LiveCD all the time, but I don't use NTFS at all, only for test purposes.
I just gave GParted a test run and made a partition with GParted LiveCD and formatted it with the NTFS fileystem and then checked it with GParted. It seems to work great. I clicked on the triangle buttons for details and it tells me all the things GParted did to check and repair the filesystem. If you like you could do the same, just make a small test partition with GParted LiveCD and then check it to see if you're happy with that or not.

GParted is the best partitioning software you can get, the developers are working to improve it even more all the time. [GParted has its own forum too]("http://gparted.sourceforge.net/forum.php"), for expert help. So if you want help from someone who knows more then me, try asking there for help. Those guys are great!  You can also look around and see what solutions others are using. You will see a few others there with NTFS problems, but keep in mind these are probably thousands of people with no problems who don't post to the forum because they didn't have any problem, of course. At least they have a public forum so you can see other people's questions and help. Commercial disk partitioning software keeps everything a secret, so we don't know they have a lot of failures maybe. I trust open source a lot more than commercial software.

Otherwise you could try taking a look around in your Windows recovery console and see if it has scandisk and defrag in it or some other Windows utilities you can run. Windows utilities are probably best for Windows and Linux utilities for Linux, but very often nowadays the Linux ones are better for everything.

I really hope it works for you, but there are no guarantees with things like this, it's something worth a try.

Regards, Herman :)

---

### Post by lumarh on 2007-03-22
thanks for all the help ill give it all a proper read and try out the mbr stuff this weekend. ive been hella busy ill let you know how it gos

---

### Post by dannyboy79 on 2007-03-22
if the original poster is still getting he NTLDR is missing error than I am guessing that either his boot.ini file is corrupt or missing and or ntldr is corrupt or missing and or his ntdetect.com file is corrupt or missing. I actually just fized this for a friend. He doesn't dual boot but that doesn't matter, the point is is that when windows is attempting to be loaded it can't find it's boot files. I was able to download a xpnt4lix.zip, extract the image and make a floppy file using linux "dd if=filename.img of=/dev/fd0"  and then I booted the floppy, there are many choices to chose from which basically looks for windows install hard disk and partition (c:\ drive), the floppy uses it's own ntdetect.com and boot.ini and then you get booted into your os. then you double click on the ntldrfix.bat or whatever it was called, then this overwrites your current ntdetect.com and boot.ini and actually does back up your current ones. then when you boot again without the floppy the list will appear again, chose the same option that you used when you got into windows and then you're in again. then you go to msconfig and change the boot.ini section timeout to 1 second and this way you won't see the list anymore and you're now able o boot into your os from now on!!! YEAH. here is the link. [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
if it works please donate 5 bucks. Thanx

My suggestion is for you to unhook your ubuntu hard drive temporarily and do the procedure, then after following all steps are done, hook up your ubuntu hard drive and boot that, then grub will appear and attempt to chainload windows since grub can't directly boot winbloz and then you'll be in again. It's fixed!! Note, make sure your menu.lst is correct after all this playing around with it. Herman can help, he's the man for dual booting.

Have you simply booted ubuntu and then mounted your windows drive to see if the boot.ini file, ntldr,  and ndetect.com files are on that drive at the highest level (these files are on the same "Level" as the Windows folder.

---

### Post by Gauvenator on 2007-03-27
I had Linux on the same hardrive as Windows, just in different partitions.  
Thanks for all your help guys, you don't have to post anymore on this for me.

---

### Post by dannyboy79 on 2007-03-28
well can you please post what you did to solve this so others can benefit from your troubleshooting this with us??? This is something that people should always do, that way people don't read thru a 5 page thread only to find at the end the person didn't put how they solved it. Hopefully you read my last post and got it working.

---

### Post by Gauvenator on 2007-05-02
Unfortunately, I was unable to fix the problem because my computer is an HP.  It didn't come with a Windows CD, and it doesn't have a floppy drive.  My family was unable to go without WinXP for any longer, so I ended up reinstalling windows with the HP recovery DVDs.  Also, there was only one hardrive in the computer.

Thanks for your help, I might have been able to fix it if I had had more time.

---

