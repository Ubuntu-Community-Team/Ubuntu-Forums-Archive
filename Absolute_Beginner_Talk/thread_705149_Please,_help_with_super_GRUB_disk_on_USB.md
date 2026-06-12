---
title: "Please, help with super GRUB disk on USB"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by darchmitt on 2008-02-23
Hello! i have a question about terminal commands to use super GRUB on a USB stick...

i recently installed ubuntu 4.10 and intended to dual boot ubuntu and win xp, but when selecting Windows xp option rather than ubuntu when starting up the computer, it doesn't boots windows...

i've been trying to use super GRUB on a usb stick, following Adrian15's instructions explained in Herman's tutorial:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#adrian15s_method:](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#adrian15s_method:)

i've done the part of comparing the information of mount command and i know that my usb stick is:
/dev/sdf1

however when trying the command:   ```
unmount/dev/sdf1
```
the output is :
```
bash: unmount/dev/sdf1: No such file or directory
```

that's my first problem.
then, i unmount the usb drive from the file manager by right-clicking the usb and then "unmount"
however when following adrian15's instructions:
```
grub
grub>device (hd3) /dev/sdf1
```
this is what i get:

```
grub> device(hd3)/dev/sdf1
device(hd3)/dev/sdf1

Error 27: Unrecognized command
```

i don't know what am i doing wrong.  so i would really thank you if you can help me.
also, don't know if you noticed (probably you did). i am a beginner with ubuntu and obviously the whole terminal thing is very confusing for me..

well, i hope someone can help.
i did look in the forum before i posted this questions and there where some like these but i couldn't find some one having such trouble with the terminal....

thanks again!

---

### Post by Herman on 2008-02-23
>  i recently installed ubuntu 4.10 and intended to dual boot ubuntu and win xp Ubuntu 4.10! That's as old as Methuselah! :)
Why don't you get yourself an up to date version of Ubuntu? Ubuntu is free, you won't have to pay more for a newer version. 
:) I still have my old 4.10 CD here, and my 5.04 discs. Someday maybe they'll be collector's items.
> but when selecting Windows xp option rather than ubuntu when starting up the computer, it doesn't boots windows...
 Do you have GRUB? Can you get [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") ?
(Try pressing your 'c' key from your GRUB menu).

Regards, Herman :)

---

### Post by Herman on 2008-02-23
:) Actually, now that I've had time to think it over, I think I'll re-install 4.10 again some time just for fun. Ubuntu has come a long way since 4.10, computers have advanced a lot too. :)

---

### Post by Mustard on 2008-02-23
It might be easier to solve the problem with GRUB not loading windows, than to solve the issue of using 'Super Grub Disk' on a USB drive.  It would be helpful to know how you have partitioned your drive or drives, which operating systems are on which partition, and the contents of your /boot/grub/menu.lst

---

### Post by Herman on 2008-02-23
```
unmount/dev/sdf1
```Ah, I see something. one of the most common mistakes for Linux beginners, it's supposed to be 'umount' without an 'n' in it. The 'n' is left out on purpose, don't ask me why, but I'll bet you thought I made a mistake in the website right? :)
Linux must have been invented by a group of practical jokers.  :)
Try,
```
 umount/dev/sdf1
```and see if that works any better.

---

### Post by Herman on 2008-02-23
> It might be easier to solve the problem with GRUB not loading windows, than to solve the issue of using 'Super Grub Disk' on a USB drive. It would be helpful to know how you have partitioned your drive or drives, which operating systems are on which partition, and the contents of your /boot/grub/menu.lst Yeah, Mustard's right, darchmitt.

Well you can do that one of two ways, you can boot Ubuntu and tell us the output from 'sudo fdisk -lu' and post the bottom half of your /boot/grub/menu.lst'
```
sudo fdisk -lu
``````
gksudo gedit /boot/grub/menu.lst
```And we can show you how to fix it.

Or you can [boot Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way") with GRUB's Command Line and write down the commands you need and edit your /boot./grub/menu.lst with the same commands.

We can help you with Super Grub Disk for USB after that.

---

### Post by darchmitt on 2008-02-23
hey thanks for all for your help...

first of all, i made a terrible mistake,,,
i messed up with the version i said i installed... it is 7.10, not 4.10 (so damn embarassing).

Herman: you are right i was typing unmount instead of umount..... damn...
i will go with what Mustard and Herman suggest so here is the out put of "sudo fdisk..."

```
darchmitt@Phanton-F4:~$ sudo fdisk - lu

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
darchmitt@Phanton-F4:~$ 

```

and here is the bottom of menu.lst :
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dfc6bf4b-774a-48d7-9258-cdc591500b6a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dfc6bf4b-774a-48d7-9258-cdc591500b6a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

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

```

hope you can help me to boot my win xp again.
and sorry for the version confusion...
and thanks for all! this really is a very helpful comunity

---

### Post by Herman on 2008-02-23
:) darchmitt, when you're typing any computer commands you are supposed to pay attention to exactly where there are punctuation marks, symbols and spaces. I suppose it doesn't make any sense to you yet, but pretty soon you'll know.  :)
For example, 'sudo fdisk - lu' doesn't work, but 'sudo fdisk -lu' will work, that command is supposed to show us an fdisk view of your partition table, which is often helpful in solving booting problems.
Also, from your first post, 'device(hd3)/dev/sdf1' didn't work, but 'device (hd3) /dev/sdf1' should have worked. :)

Anyway, I still can't see why your Windows won't boot, so I can't help you yet. Your menu,lst file looks okay to me.
I can't really tell without the proper fdisk output, but I guess it's okay.

What happens when you try to boot Windows? 
What error messages do you get exactly, or what do you see? A blues screen with something written on it, or a black screen?

When you boot Ubuntu, can you 'see' inside your Windows partitions? (By clicking the white icons on your Desktop? 
Do they look something like this, [            A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...showing the important files needed for booting. 
Can you see the important Windows booting files there in both of your Windows systems? NTLDR? NTDetect.com? boot.ini? If those are there things will be easier, but sometimes Windows copies them out.

I'd still like to see your 'sudo fdisk -lu' output please, if you can,
```
sudo fdisk -lu
```Regards, Herman :)

---

### Post by darchmitt on 2008-02-23
Herman:

sorry again... i now realize my mistake.
here is the output of  sudo fdisk -lu

```
$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   352819529   176409733+   7  HPFS/NTFS
/dev/sda2       372148560   390715919     9283680    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       352819530   371230019     9205245   83  Linux
/dev/sda4       371230020   372145724      457852+   5  Extended
/dev/sda5       371230083   372145724      457821   82  Linux swap / Solaris

Partition table entries are not in disk order
```

when i select windows from the GRUB menu, it says "starting up..." (black sreen) and it just keeps like that, windows won't boot.

i've already tried using super GRUB disk burnt on a dvd, but when choosing to boot windows, same thing happens: "Starting up..." and stays like that.

i've also done this:

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way)

from the grub command line... but same thing happened after giving it the "boot" command.. 

I can see the Windows partition from ubuntu, i can see the NTDETCT.COM, ntldr and boot.ini on the root folder of the windows partition..

Also.. i don't have two windows systems... on the GRUB menu two Windows options appear, one is "Windows XP Media Center Edition" and the other one is "Windows NT/2000/XP" which when selecting this one, i found its an HP Recovery tool that came with the pc (is a partition that was always there, i think it is /dev/sda2 because that "recovery" partition was the only FAT32 partition that i knew about on my internal disk.).

Maybe i should have told you the whole story....
You see about 2 or 3 months ago i installed Ubuntu on an external (usb conected) hard disk with the intention of not messing up windows and the files on the internal disk. However i later read that when attempting such thing, one must unplug the internal disk so that when installing Ubuntu, the only detectable disk would be the USB external hard disk, but at the time i did not know that. So i installed Ubuntu on the USB external hd but without unplugging the internal disk and when trying to restart after installation there was a GRUB error 21 when starting up. 
Later someone from this forum referred a similar post and i managed to boot both windows or ubuntu from GRUB but only when the external hd was connected. I leave the pc that way for those 2 or 3 months, needing to have the ubs hard disk connected every time i wanted to stat up the computer (with either win xp or ubuntu).
Then i decided to reinstall Ubuntu on the internal HD so that i can restart the computer without the external hd connected (i figure not to use the external hd anymore). So i installed ubuntu 7.10 but now in the internal hd with the external hd unplugged. The installation went O.K. however the problem raised when trying to boot Windows XP, which won't boot and is my current problem.

well that's the story...
i hope you can help me.
thanks for your patience man, i am very embarrassed for the command mistakes, I'll be careful in the future.

---

### Post by Herman on 2008-02-23
> when i select windows from the GRUB menu, it says "starting up..." (black sreen) and it just keeps like that, windows won't boot.
i've already tried using super GRUB disk burnt on a dvd, but when choosing to boot windows, same thing happens: "Starting up..." and stays like that.
i've also done this: [http://users.bigpond.net.au/hermanzo...the_simple_way]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way")
from the grub command line... but same thing happened after giving it the "boot" command..  AHA! I wonder if your Windows boot sector is okay? Thanks for trying those experiments and letting me know, that's a big help.
You can fix your Windows boot sector if you have your Windows installation CD.                 Just put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the 'FIXBOOT' command.
If you don't have a Windows 'Installation' disc, (since obviously you have a recovery partition instead), you should be able to boot Windows with an NTLDR CD. Go to this website here, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"), and download an .iso file for a CD from there or else a file for a floppy disk or USB drive. Those have NTLDR, NTdetect.com and a generic boot.ini file in them, something like a Windows version of Super Grub Disk, but with Windows booting files. Those can bypass the MBR, the boot sector, boot.ini and NTLDR and NTDetect.com, so they will almost certainly boot your Windows XP for you.  Then you can try to get into recovery console from there somehow and repair the boot sector. Maybe by pressing your F8 key during boot-up?

I know that Windows keeps a spare boot sector in the FAT32 file system nd that can be used to restore the boot sector from Linux with the right commands. I have read that Windows keeps a spare boot sector when you are using the NTFS file system too, but it's at the end of the partition somewhere I think. I would need to do more research to find out exactly where it is. A 'dd command might be able to restore your boot sector from that, but I'm not sure, I would need to read a lot first and it would be best to try that out in a system no-one cares about before using it in a real system, but there is always hope, there are alwys lots of different ways to fix things.

I'm only guessing the problem is your boot sector, even if I'm wrong, restoring the boot sector with FIXBOOT won't hurt anything, apart from possibly being a waste of time, but I'm hoping that might fix it. I don't know how anything could have happened to your boot sector though.

> I can see the Windows partition from ubuntu, i can see the NTDETCT.COM, ntldr and boot.ini on the root folder of the windows partition. Good, thank you for looking for me and letting me know, thanks for the other information too, it is all might be very helpful.

One problem I can see in your partition table is that partition 2 doesn't end on a cylinder boundary, but I don't think that would stop Windows from booting in partition 1, so we'll just ignore that for now.
```
$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   352819529   176409733+   7  HPFS/NTFS
/dev/sda2       372148560   390715919     9283680    c  W95 FAT32 (LBA)
[COLOR=Red]** Partition 2 does not end on cylinder boundary.**[/COLOR]
/dev/sda3       352819530   371230019     9205245   83  Linux
/dev/sda4       371230020   372145724      457852+   5  Extended
/dev/sda5       371230083   372145724      457821   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by darchmitt on 2008-02-23
Thanks again Herman, you've been very kind at helping me.
I don't want you to get into the trouble of reading a lot just to help me, please don't, i already feel i owe you a lot.

I think i can go with the Recovery Console and try the FIXBOOT... i do not have a Win Xp Media Center edition installation cd (or at least not one included on the pc purchase), but i do have a Win XP (not media center edition) from another pc. Can i use that one?
(i know probably Recovery Console tools will be the same for diferent XP versions but i don't want to assume too much)

also, if i use FIXBOOT, will i still be able to boot ubuntu? (If not, it doesn't matter right now, i'm only trying Ubuntu, right know my priority is getting Win XP to boot)

thanks again man!!!

---

### Post by Herman on 2008-02-23
> I think i can go with the Recovery Console and try the FIXBOOT... i do not have a Win Xp Media Center edition installation cd (or at least not one included on the pc purchase), but i do have a Win XP (not media center edition) from another pc. Can i use that one?
(i know probably Recovery Console tools will be the same for diferent XP versions but i don't want to assume too much) I am fairly certian that all Windows CDs will do the same job when you run the FIXBOOT program, so it shouldn't matter what computer it's from or which version it's for. Otherwise they would probably have to think up a new name for the program.

> also, if i use FIXBOOT, will i still be able to boot ubuntu? (If not, it doesn't matter right now, i'm only trying Ubuntu, right know my priority is getting Win XP to boot):) You will still be able to boot Ubuntu. Windows boot sector only affects Windows. As long as you run the FIXBOOT command it will only restore the Windows boot sector.
Don't use the FIXMBR command though, because that will corrupt your MBR, (Master Boot Record), and you'll have to re-install GRUB to fix it again. The MBR doesn't belong to Windows, it belongs to the whole hard disk, and the hard disk belongs to the owner of the computer.

I hope FIXBOOT will fix it for you. Good luck! If it doesn't we'll just have to keep thinking and trying other ideas.

Regards, Herman :)

---

### Post by Herman on 2008-02-23
>  I don't want you to get into the trouble of reading a lot just to help me, please don't, i already feel i owe you a lot.:) Hey, don't worry about me, I read a lot because I'm curious about things and I just like learning.
I found a web page that had the information I was looking for, [FONT=Times New Roman, Times, serif][B][Location of an NTFS Volume's *"Backup"*      Boot Sector]("http://mirror.href.com/thestarman/asm/mbr/NTFSBR.htm#BSback"). 
[/B][/FONT]The back-up boot sector for a Windows partition with an NTFS file system is in the very last sector of the partition. I think that's interesting, probably we could make up a 'dd' command for restoring the boot block now that we have that information. I know that 'dd' commands need to be used with great care, so we'll just save that little gem of knowledge for someday when someone really needs it. :)

EDIT: [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is a program which is installable in Ubuntu. Testdisk can be used to restore a corrupted NTFS boot sector from it's backup safely and easily, [NTFS Boot sector recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery")

---

### Post by darchmitt on 2008-02-24
Hello again.

Oh, good to know you read for curiosity jeje :)
I have bad news... i tried using the Fixboot command on the windows recovery console but it did not solve the problem. Then, i made it worst... in a desperate attempt to fix this problem once and for all, i then used the Fixmbr command too, (i know you told me not to use it... i kinda loose my temper...) so know GRUB is not there and i have to boot ubuntu using super Grub disk (thank god i made a copy).

Later i decided to back as much as i could and then be prepared for the worst, so i burnt about 13 or 15 DVDs with the important documents. Then boot using the SGD to the other "windows" partition, the one that is the "recovery" partition and started the "recovery" process... i thought it would format the whole disk and install windows the way it was like when just purchased but apparently there was no effect... I'm not sure of what this "recovery" process did,,, i can still see the files of the windows partition and everything seems the same.

well, that's what has happened until now...
i am now seriously thinking to use any method that would wipe out everything on the hard disk and install Win XP (since i have the important documents backed up). I believe this method is reinstalling Windows XP...

well, meanwhile i'll give TestDisk a try...

actually since i can't boot win xp i've been using ubuntu for the past couple of days and i like it! however since this computer belongs to my dad, it won't be late 'till he starts asking when will he'll be able to use it again...
actually he does not use it very often, he just read mail, use some word or excel documents, the regular stuff... but still he won't use it until he look the usual XP interface..

well, i'll keep up to date with this problem,

thanks a lot again man!!!

---

### Post by Herman on 2008-02-24
Windows operating systems are really weird and moody. Sometimes they just refuse to boot, seemingly for no good reason at all, 'just because'. I had a problem something like the one you have with a friend's (Windows) computer which just needed some partition resizing done and a defrag.
The partition resizing went fine and the computer rebooted okay but after I ran defrag it wouldn't reboot. Now a defrag shouldn't have hurt it. 
I thought maybe it needs CHKDSK, but I didn't have a Windows 'Installation CD', only those 'Recovery ' disks, so I had to make my own BartPE Windows Live CD and then make a Windows installation disk from that before I could even run a simple file system check. It took me all weekend. (It only started as a five minute resize job). I ran CHKDSK but it didn't help. (Pull hair).
Eventually I worked out how to boot into safe mode and it booted!
After a lot more messing around and reading weird senseless error messages and tracking them down it eventually turned out that the (well know brand of) antivirus messes with the display drivers for some strange reason and it didn't agree with the display settings (which I hadn't touched) and had nothing at all do do with anything I did. Unless defragging made it work well enough to install a bad automatic update or something.  Anyway, all I had to do was turn that off and it was fixed. Proprietary software doesn't  work very well, it seems.

Anyway, try tapping your F8 key while trying to boot and see if you can get a menu to switch into 'safe mode' and boot. That might work.

Have you tried the  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") link yet? That should get it to boot.

I would leave TestDisk until later maybe, because FIXBOOT should have fixed you boot sector already, there might be some other silly reason why Windows won't boot that we haven't thought of yet, something like I explained above. 

Regards, Herman :)

---

### Post by darchmitt on 2008-02-24
Wow, what a problem that of the antiviruses messing with the display! I can't believe these problems are so damn difficult to solve... This is really the first time that a computer fails to me this way. I usually can handle any other problem (viruses, space running out, etc,), but never had a problem booting windows. 
Now, i am 100% sure it has to do with ubuntu being installed so i probably stay focusing on that. Before i couldn't boot windows any more, everything was OK: i defrag the disk almost once every month, run CCleaner every week and i even free up about 30 GB before reinstalling Ubuntu. So i am convince the pc is or was in pretty good shape and the problem was generated when reinstalling ubuntu. 

hey Herman, I've though of something.... i'm not sure if it'll work though...
If you recall, the first time i installed Ubuntu was on an external hard disk, and from then on, the only way to boot either ubuntu or windows was having the usb hd plugged. Then i reinstalled ubuntu on the internal hard disk and messed up GRUB and now i only can boot ubuntu using SuperGrub Disk.  However, on the external hdd, there still are the ubuntu OS files. Wouldn't it help comparing the "menu.lst" (or any other boot related file) of the external hard disk with that of the internal hard disk?

i'm gonna try to boot using the external hard disk and super grub..

if no good, i'll try the "How to fix: NTLDR is missing, press any key to restart " you suggested.

well, thanks again for all your help!!!

---

### Post by darchmitt on 2008-02-25
Hello again Herman.

You'd be happy to know that everything is OK now.... well, sort of...

After thinking about it and running out of time, i decided to wipe the whole disk and reinstall winXP. I figure that since i had everything backed up, it wouldn't be that much of an inconvenient. As a matter of fact, i think it is much better now, obviously because its practically a fresh new PC.

I'm sad though, because of the lack of Ubuntu, but i suppose i will try a dual boot somewhere in the near future, but this time with the proper cares and information on how to do it. If i try it i will follow your tutorial. For now, though i'm praising and holding to windows, cause i thought i could never fix this thing...

I am seriously considering buying a "cheap" pc to try the dual boot without affecting other people, i'll probably do that...

All that remain is to thank you for all your support and most of all, for your patience and sincere interest in helping me. I actually cannot believe you replied that many times, like if the problem where your's and not mine, lol.  I can see now that this community is indeed a example for others.

Thanks man!!!
i'll be around in the forum from now on, trying to learn as much as i can

greetings from México!

---

### Post by Herman on 2008-02-25
:) Hello darchmitt,
>  After thinking about it and running out of time, i decided to wipe the whole disk and reinstall winXP. I figure that since i had everything backed up, it wouldn't be that much of an inconvenient. As a matter of fact, i think it is much better now, obviously because its practically a fresh new PC. Yes, it does seem to do Windows a lot of good to be given a nice clean re-install every now and again. I'm sorry you had to do that this time though, because I remember it can be a lot of work, or at least time consuming.
> I'm sad though, because of the lack of Ubuntu, but i suppose i will try a dual boot somewhere in the near future, but this time with the proper cares and information on how to do it. If i try it i will follow your tutorial. For now, though i'm praising and holding to windows, cause i thought i could never fix this thing... Yes, I'm sad you couldn't keep Ubuntu too. I wonder what was wrong, Ubuntu doesn't write to the Windows partition, so it was an unusual problem. 
>  I am seriously considering buying a "cheap" pc to try the dual boot without affecting other people, i'll probably do that...:) Yes, that sounds like a good idea! 
> All that remain is to thank you for all your support and most of all, for your patience and sincere interest in helping me. I actually cannot believe you replied that many times, like if the problem where your's and not mine, lol. I can see now that this community is indeed a example for others.

Thanks man!!!
i'll be around in the forum from now on, trying to learn as much as i can

greetings from México!:) Okay, no problem! Thanks for your excellent co-operation as well. I enjoyed helping you and there are lots of other people here in Ubuntu Web Forums who enjoy helping people too.
From Mexico eh? I have a cousin living in Mexico somewhere. 
Well bye for now, all the best, I hope you get Ubuntu sometime soon, normally goes in most computers with no problems.

Regards, Herman  :)
Greetings from Australia!

---

