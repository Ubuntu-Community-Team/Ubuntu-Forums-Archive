---
title: "Working with two Hard Drives"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Khane on 2006-05-08
I have visited this forum some time ago , asked a few questions but until now I did not give Ubuntu or any other Linux distribution a try. Very recently I upgraded my computer and bought a new Hard Drive. I want to keep Windows XP on one HD and install Ubuntu on the second one.

. How I'll be able to switch between my XP's Hard Drive right to my Ubuntu Hard Drive? Is there an easy way to do so ? Do I have to reboot heach time I want to  switch  from one HD to the other ?
. Is it possible to transfer files I create in Ubuntu to my XP'd Hard Drive and vice versa ?

If you are trying to help me, please try to do it with the less technical language possible; my knowledge of computer related stuff and jargon is very minimal :sad: 

Thank you very much in advance.

---

### Post by mips on 2006-05-08
[QUOTE=Khane]
. How I'll be able to switch between my XP's Hard Drive right to my Ubuntu Hard Drive? Is there an easy way to do so ? Do I have to reboot heach time I want to  switch  from one HD to the other ?
[/QUOTE]

You have to reboot each time. When you install ubuntu it will ask you to install a grub boot loader on the windows drive. this will give you a menu to select which OS you want to boot. 
Alternatively you can use VMWare to run windows inside of Ubuntu on a virtual machine/pc which does not require a reboot. This way windows will be running inside a window on Ubuntu which is pretty cool and allows you to access both at the same time.


[QUOTE=Khane]
. Is it possible to transfer files I create in Ubuntu to my XP'd Hard Drive and vice versa ?
[/QUOTE]
Yes as long as the XP file sysyem uses FAT32 then you can write to the windows drive. If XP uses NTFS you can only read from the windows drive.
From windows you will have to install a driver to read the linux file system. EXT2IFS will do this.

If you are trying to help me, please try to do it with the less technical language possible; my knowledge of computer related stuff and jargon is very minimal :sad: 

Thank you very much in advance.[/QUOTE]

---

### Post by Khane on 2006-05-08
Hi mips,

Thanks for helping
Khane

---

### Post by confused57 on 2006-05-08
Khane,
    You have a couple of options of how you can set up a dual boot with 2 hd:

1.) You can install Ubuntu to the 2nd drive and install Grub to the windows mbr

or

2.) If you don't want to chance installing Grub to your windows you can follow the guide in these threads(check the advice by "lha"):

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

---

### Post by Khane on 2006-05-17
Hi

First , **confused67**, if you read this post then I would like to thank you very much for your reply and the useful links you gave me.

It's been a week now since my last post and today I tried to install Ubuntu for the first time but before the installation process really started I encountered a first problem. As I explained in my previous post , I have new computer since a week now and it arrived with a brand new 160GB hard disk on which I installed Windows XP. Today I also installed my previous120GB hard disk in my computer to install Ubuntu inside (right now Windows XP is still installed on that disk also).  After I made a backup of what I still need from that disk I went to install Ubuntu on it. I started the Ubuntu's installation following the instruction of a book called "Beginning Ubuntu Linux - From novice to professional" and I arrived at a screen asking me to chose where to install Ubuntu and these are the options the screen gives me.

Resize SCSI1(0,0,0,0), partition #5 (sda 5)  and use freed space
Erase entire disc: IDE2 master (hdc)  - 120.0GB WDC-WD 1200JB
Erase entire disc: SCSI1 (0,0,0)  (sda)     - 160.0GB ATA  WDC ....
Erase entire disc and use LVM : IDE2 master (hdc) - 120.0GB WDCW...
Erase entire disc and use LVM: SCSI1 (0,0,0) (sda) - 160.0GB ATA
Use the largest continuous free space
Manually edit partition table

The author of the book that I am following the installation instructions, especially says that in the case that Windows and Ubuntu are installed on two different hard disks it is very important to make sure **not** to select any option related to the master drive and that Ubuntu should be installed on the **"slave" drive** only. As far as I understand, none of my two hard disks is right now defined as **slave**. The hard disc I want to install Ubuntu on is defined as **master** drive and  the other one, my 160GB hard disk is neither defined as slave nor master (at least according my very small understanding of PC related things). The only disk defined as slave, according the BIOS, is one  of my two DVD drives.
What should I do to make my 120GB hard disk a slave drive and my 160GB hard disk a master drive ? By the way why is my 120GB disk that I installed today defined as "master" and not the other hard disk? There is certainly a logic behind that but I have no idea what it is.
What is the "**Erase entire disc and use LVM**" option for ? Should I pick this option or not and why ?

Thank you very much in advance.

---

### Post by Topaz on 2006-05-17
If I follow what you stated, you have 2 harddrives with winxp on them and you installed
the second drive. Forget about installing linux for a minute. Start your computer and
open explorer that shows your different drives. See if you see all your harddrives and cd, dvd, and whatever drives you have. If you do check and note the size, the second
harddrive I believe is the one you want to put linux on. So that is the one that gets reformated and your new os installed on after you have saved files you want for your other harddrive.

---

### Post by confused57 on 2006-05-17
Don't do anything quite yet, until you get a reply from an expert, I'm pretty new at this.
My observations to give you some idea:

You'd want to select "Erase entire disk...WD 120G.." to install Ubuntu onto(Ubuntu will overwrite the windows on this drive), when the installer asks where to install Grub, select the drive with Windows on it (the 160G SATA drive).

Master and slave do not apply to SATA drives, which is what the drive with windows is(160G).

Do not use the LVM option.

Wait a little to see if you get any other replies...

You may want to read over this guide before beginning:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Read over the above dual-boot guide, see if anyone replies that can give you more specific instructions; ask more questions if anything's not clear.

---

### Post by Khane on 2006-05-17
[QUOTE=Topaz]open explorer that shows your different drives. See if you see all your hard drives and cd, dvd, and whatever drives you have. If you do check and note the size, the second harddrive I believe is the one you want to put linux on. So that is the one that gets reformated and your new os installed on after you have saved files you want for your other harddrive.[/QUOTE]

According Explorer I have two hard disks : one is the the new 160GB disk (partitioned in two drives C: 40GB and D: 120GB) with Windows XP and the second hard disk is my old 120GB disk (partitioned right now in three drives - 40GB + 40GB  + 40GB) also with Windows XP installed on, and that's the one I want to completely delete Windows from and install Ubuntu instead. There are also my two DVD drives.

Since the 120GB drive is defined as the "master drive" by Ubuntu installation and I **should not** install Ubuntu on a master drive but **only** on a **slave** drive, I would like to know how to transformed my 120GB disk into a "slave drive" so I can install Ubuntu on and how to make my 160GB the "master drive"?

Thanks

---

### Post by fornix on 2006-05-17
> Since the 120GB drive is defined as the "master drive" by Ubuntu installation and I should not install Ubuntu on a master drive but only on a slave drive, I would like to know how to transformed my 120GB disk into a "slave drive" 
In your case, its different. What the book means is that u should not install it in master (Here master refers to the drive which gets access whlie booting your PC) In your case This master is ur sata drive. And your 128GB drive is "IDE" master. If both ur HDD were IDE, then u should not install on master. but in ur case u can go ahead and install linux on ur "master" 120 GB drive and then after installation, it will ask you where to load the GRUB boot loader. Now u need to choose /dev/sda it should work. But be a bit cautious because i have not tried it with a SATA and an IDE drive combination. 

If at all something goes wrong and ur windows wont boot, u can put in ur windows XP CD and go to recovery console, type
```
fixmbr
```

It should restore ur Master boot record and should start XP the normal way. Please clear all your doubts before trying or if you like experimenting, go ahead, screw ur system and then fix it. Its a fun way to learn though not recommended :p

---

### Post by confused57 on 2006-05-17
I believe I found a link that may help you:

[http://ubuntuforums.org/showthread.php?t=46003&highlight=SATA+dual+boot](http://ubuntuforums.org/showthread.php?t=46003&highlight=SATA+dual+boot)

The end result, I think, is the same as if you followed the 2 links(read instructions by "lha") I gave you a week ago; but just a different method.  You may want to reread the 2 links before you decide which you want to use.

I have the same book by Keir Thomas and it doesn't really cover dual-booting with 2 hd when one is a SATA drive.  Following the links I gave you, if something goes wrong, you can always unplug the Ubuntu drive and your computer should boot into windows since Grub isn't installed on the windows SATA drive.

Basically, to install Ubuntu using the 2 links I suggested earlier, you'd disconnect the SATA drive and only have the IDE 120G connected when installing Ubuntu.  After you have Ubuntu running the way you like, add the windows boot entry to grub menu.lst(see links).  Shutdown your computer, reconnect the SATA drive with windows, make sure in bios that the Ubuntu IDE drive is the 1st hard drive that the computer boots into.  Good Luck... let us know how things turn out...

> Since the 120GB drive is defined as the "master drive" by Ubuntu installation and I should not install Ubuntu on a master drive but only on a slave drive, I would like to know how to transformed my 120GB disk into a "slave drive" so I can install Ubuntu on and how to make my 160GB the "master drive"?

When windows and Ubuntu are dual-booted on the same HD, windows has to be installed 1st and onto the first partition.  With 2 IDE HD's, if you install Ubuntu on the 2nd drive; it's best to have windows as the master(with Grub) and Ubuntu as the slave(for the same reasons as both OS on a single drive).

If you use the method(s) I've provided as an option, you don't modify the windows mbr;  the windows grub menu.lst entry has mapping commands, which fools windows into thinking it is on the master drive.

If you use the method in your book, it may work if you install grub onto the mbr of your windows SATA 160G and make sure your bios is set to boot 1st from the SATA drive.

I don't really know, but at least you have some options...

---

### Post by Khane on 2006-05-18
Thanks you all for helping

I'll soon install and I hope that my next message will be from Ubuntu ;) 

khane

---

### Post by Khane on 2006-05-18
I am back and still from Windows XP :( 

I tried to install Ubuntu but I did not go very far into the installation process...I reached a screen reading :


[b][i]Partition Disk

If you continue , the change blah blah blah...

The following partitions are going to be formated
Partition #1 of IDE master(hdc) as ext3
Partition #5 of IDE master(hdc) as swap[/b][/i]

I answered "YES to the partitioning and right after I got a screen that  reads:

[b][i]Input/output error during read on
/dev/ide/host0/bus/target0/luno0/disc

ERROR !!

Retry
Ignore
Cancel[/b][/i]

I tried the "Retry" option three times and got the same ERROR!! screen again. Then I tried "Ignore" option; on the third "Ignore" attempt I got a screen reading:

***The creation of swap space in partition #5 of IDE2 master (hdc) failed***.

Any idea what the problem is and what is the solution?

Thanks in advance
khane

---

### Post by confused57 on 2006-05-18
You may have a bad sector on your hard drive.  You could try using the manual partition option...or you could try a livecd and use gparted to partition the disk.

Which method are you using to install Ubuntu?

---

### Post by Khane on 2006-05-18
[QUOTE=confused57]You may have a bad sector on your hard drive.  You could try using the manual partition option...or you could try a livecd and use gparted to partition the disk.[/QUOTE]

I'll try the live CD and gparted

> Which method are you using to install Ubuntu?

What do you mean by "which method" ? :???:

---

### Post by confused57 on 2006-05-18
1.)Both drives connected, installing to IDE 120G drive

2.) This method:
        [http://ubuntuforums.org/showthread.php?t=46003&highlight=SATA+dual+boot](http://ubuntuforums.org/showthread.php?t=46003&highlight=SATA+dual+boot)

or

3.) This method:

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

I don't think the method you're using has anything to do with the error message, but the info may help.  I'm assuming you must be using method 1.  If you want to see some screenshots of manual partitioning, look over the dual-boot guide provided in an earlier reply.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Khane on 2006-05-18
I was trying this method:
[http://ubuntuforums.org/showthread.p...SATA+dual+boot](http://ubuntuforums.org/showthread.p...SATA+dual+boot)

If that's really a bad sector problem then what gparted can do better than the normal install CD?  Is there a way to fix bad sectors?

khane

---

### Post by confused57 on 2006-05-18
You're absolutely correct, the install CD can do the partitioning manually for you.
It'll be a learning experience for you, but you could try the manual partitioning option during install, just be sure to create a swap partition(approx. 2x the amount of ram you have) along with the root(/) partition.  You'll need to create the root partition first, then the swap partition.

I was just mentioning a bad sector "may" give you this error, I don't know for sure.  If by chance it is a bad sector near the end of your drive, you could try a smaller root partition(+swap) and have free space at the end of your drive.  I think you can go back, if the installation is successful, and partition & format the free space.  I'm just trying to give you some ideas to try if you feel adventurous.  With my limited knowledge, I'm running out of ideas...and I definitely can't guarantee anything I've suggested.  Be patient...someone'll probably see this thread who has the experience to help you.

Check out this link for partitioning:

[http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#createditpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#createditpartgparted)

---

### Post by Khane on 2006-05-18
I tried the Ubuntu Live CD on my new hard disk but there too things went wrong. The setup reached the cool brown and yellow graphic screen ( with the Ubuntu logo  and a bar showing the status of the process) there I saw that every thing went fine except "Synchronizing clock"(no idea what that means) that got a red "failed". I then was asked to pick my screen resolution , I clicked on 1280x1024 (my LCD native resolution) and clicked OK. An other screen appeared (kind of DOS screen) and here  I got that :

***Failed to start the X Server ( your graphic interface) It is likely that...etc...etc...*** I clicked on YES when asked if I want to see the diagnosis , which brought me to a screen with a lot of technical details (many X's and figures of all kind) all in English but with no meaning for me.
It seems that I have no luck with Ubuntu. :confused: 

> Be patient...someone'll probably see this thread who has the experience to help you

I am very patient ;)


khane

---

### Post by confused57 on 2006-05-18
Good that you're patient...you did the right thing by trying to run the liveCD, because you would get the same problems when trying to install.  I would recommend anyone new to Ubuntu to try the liveCD, make sure it works on their system, and use it for couple of weeks to get familiar with it.

You need to give us some of your system specs, makes it a little easier to help someone out,  e.g.  video card, memory, mobo, internet connection(wireless or not), etc.

I think the problem you're having with the liveCD is related to your video card & can most likely be corrected by using the correct driver.

When you get to the configuration screen after clicking "yes" from the error message, look for a place to enter a video driver.  You might want to try "vesa", "nv"; or if your card is ATI, you can try "ati" or "radeon".

If this doesn't work, you can try pressing "Ctrl+Alt+F1", which should get you to a text command prompt.
You can try typing  "sudo dpkg-reconfigure xserver-xorg"(without quotes) at the prompt...I'm not sure about the sudo using the liveCD.  This should open up an interactive menu to enter a driver & check your screen resolutions selected.   Typing in "startx"(without quotes) at the prompt should start Gnome, if the correct driver for your video card is selected.  Or pressing "Ctrl+Alt+F7" should startx.

---

### Post by Khane on 2006-05-19
[QUOTE=confused57]You need to give us some of your system specs, makes it a little easier to help someone out,  e.g.  video card, memory, mobo, internet connection(wireless or not), etc.[/QUOTE]

AMD Athalon 64 3500 939PIN
Motherboard Gygabyte GA-K8N-SLI
Memory: Hynix Dual 2x512MB DDR 400Mhz
Hard drive: Western Digital 160GB SATA-2 7200RPM,8MB
Geforce 7600GT 256MB Realtek WindFast
Monitor Samsung 930B
ASDL Alcatel modem Speed Touch Home

I installed the drivers for my 7600GT display card from the CD that came with the card. Sorry for the maybe stupid question but maybe there are special display card drivers for Linux?

khane

---

### Post by confused57 on 2006-05-19
See if this helps:

[http://www.ubuntuforums.org/showthread.php?t=176571&highlight=GeForce+7600GT](http://www.ubuntuforums.org/showthread.php?t=176571&highlight=GeForce+7600GT)

The drivers you installed from cd were for windows, not linux...the link provided may give you some idea how to install the correct linux drivers.

If your video card is PCIe and you get it working using the above link, you may be able to install the correct drivers later using this link:

[http://www.ubuntuforums.org/showthread.php?t=33142&highlight=PCI+Graphics](http://www.ubuntuforums.org/showthread.php?t=33142&highlight=PCI+Graphics)

---

### Post by Khane on 2006-05-19
**confused57**

Thank you very much for taking you time to help me :) 
I'll check the link later when I come back home 

khane

---

### Post by vipin on 2006-05-19
I suggest that you install Ubuntu on your 160 GB HDD and Windows XP with it also. This is bcoz I also had a similar problem like yours and I had three harddisks instead of two. There were a lot of problems with them bcoz there were so many Windows Partitions and ubuntu used to detect only one of them (WinXP Partition).
So I suggest you to install Windows XP and Ubuntu Linux on the 160 GB HDD with the sizes as you may require. (First WinXP and then Ubuntu).
While installing Ubuntu, don't forget to choose the file system as ext3, choose swap area, then choose a partition space for FAT32 (FAT16, i think, with mount point /windows) partition. this partition can be equally accessible by both Windows and Linux and you can write on them using both Linux and Windows.  
i hope it may help you.

---

### Post by Khane on 2006-05-19
[QUOTE=vipin]I suggest that you install Ubuntu on your 160 GB HDD and Windows XP with it also[/QUOTE]

Maybe by the end that's what I'll have to do but I still want try a few more times to install it on the 120GB drive.

> choose a partition space for FAT32 partition. this partition can be equally accessible by both Windows and Linux and you can write on them using both Linux and Windows.
Do you mean that I should create a new partition on the part of my HD on which I have Windows XP and format it FAT32. That means that the Windows XP part of my PC will have two formats; one or two NTFS partitions and an other partition FAT32. And of course Ubuntu on an other partition.


**confused57**
I hope that the problem I had running the Live CD is a drivers for Linux problem and that the link you provided will help but I just remember now that two weeks ago when I was still working with my old computer (old everything - graphic card, PCU, HD, monitor etc...) I did succeed then to run the Ubuntu Live CD (but failed to connect to the Internet) and I played around with the desktop, opened this and that, tried a few things , all that without installing any graphic drivers for Linux.

khane

---

### Post by Khane on 2006-05-19
[QUOTE=confused57]When you get to the configuration screen after clicking "yes" from the error message, look for a place to enter a video driver.  You might want to try "vesa", "nv"; or if your card is ATI, you can try "ati" or "radeon".

If this doesn't work, you can try pressing "Ctrl+Alt+F1", which should get you to a text command prompt.
You can try typing  "sudo dpkg-reconfigure xserver-xorg"(without quotes) at the prompt...I'm not sure about the sudo using the liveCD.  This should open up an interactive menu to enter a driver & check your screen resolutions selected.   Typing in "startx"(without quotes) [/QUOTE]

Gee! I thought I did it and that in a few seconds Ubuntu will start but again I got a error/fatal error message.
I ran the Live CD once more and reached again the brown and yellow graphic screen with the Ubuntu logo and the progress bar and then again I got the ***Failed to start the X Server ( your graphic interface) It is likely that...etc...etc...***. In the DOS like screen in which the last line was ***checking battery state...[ok]** and at the line after a "**ubuntu@ubuntu:~ $ -**", I typed "sudo dpkg-reconfigure xserver-xorg" -> Enter  and I started to go through the interactive menu and enter my driver (there I picked the "**nv**" since I believed that's for nvidia ) etc... By the end when I reached once more time a "ubuntu@ubuntu:~ $ -" I entered "**startx**" and was really hoping to reach the Unbutu desktop but instead I got a new error message:

[b]Fatal server error:
no screens found
XIO: fatal error IO error 104(connection reset by peer)on X server :0.0 after 0 request(0 known processed) with 0 events remaining
ubuntu@ubuntu:~ $ -[/b]

I won't say that I am not frustrated after these many unsuccessful  attempts  but I really want to succeed to run Ubuntu and in no way I'll give up trying.

khane

---

### Post by confused57 on 2006-05-19
After pressing Ctrl+Alt+F1 and get to the prompt;

enter
```
sudo /etc/init.d/gdm stop
```

then
```
sudo dpkg-reconfigure xserver-xorg
```

you could try "vga" or "vesa" for a driver

when you're back at the command prompt
enter
```
sudo /etc/init.d/gdm start
```

Give it a try.

---

### Post by Khane on 2006-05-19
**confused57**

I'st done!I am finally sending this message from Ubuntu. My error was to pick "**nv**" (for nvidia) as my driver. In one of the threads that you directed me to I found something about picking"**vesa**" instead of "nv"
I know that this is a Live session but is there any way to save something so next time I reboot from Windows to Ubuntu I won't have to go through all these setup screens to log in ?

Thank you very much for helping. Now I am going to play a bit with Ubuntu. I have a lot to learn and I'll certainly be back soon with new questions :mrgreen: 

khane

---

### Post by confused57 on 2006-05-19
Whew, I was about out of suggestions.  Good work, Khane...now you know that you'll be able to get an Ubuntu install working...work with the live CD for awhile & familiarize yourself with the OS.

The Breezy LiveCD doesn't allow you to save settings, but I think the Dapper LiveCD has something called "Persistent Session" that you can save configuration settings onto a USB flash drive(or maybe your hd, not sure) & you don't have to set everything up again each time you use the liveCD.  Who knows, the Dapper LiveCD may recognize & set up everything automatically?

Here's a great guide for downloading & burning .iso's:

[http://psychocats.net/ubuntu/windowstoubuntu.htm](http://psychocats.net/ubuntu/windowstoubuntu.htm)

Take your time, learn the OS...then when you're ready to install, consider your options...dual boot with windows on the same hd & maybe you can use the extra drive formatted with FAT & share with Ubuntu & windows for storing data...

---

### Post by Khane on 2006-05-20
[QUOTE=confused57]
The Breezy LiveCD doesn't allow you to save settings, but I think the Dapper LiveCD has something called "Persistent Session" [/QUOTE]

Thanks for the hint. I am downloading Dapper LiveCD right now

> dual boot with windows on the same hd & maybe you can use the extra drive formatted with FAT & share with Ubuntu & windows for storing data...

I understand that but if I chose to work with two HDs (one with Windows and one with Ubuntu) can I copy data from Ubuntu on a RW CD and then paste it on a one of the Windows partitions that I specially formated FAT32 for sharing?

khane

---

### Post by c3genesis on 2007-08-25
ive tried the live cd as well hoping that i could use that instead, but i get an error message saying: failed to start the xserver.  ive read many threads about this and most of the time, people are advised to use the command "sudo /etc/init.d/gdm stop"
then "sudo dpkg-reconfigure xserver-sorg"
then "sudo /etc/init.d/gdm start"
when i try the first command however, it says that the command is not recognized. am i mistyping something? have you heard of these commands? i have also been advised to use the second command by itself, but this doesnt help either.  i go in and put in vesa or ati or nv, none of them work, then i put in 600x800, 1024x768 and 1280x800 for my screen resolutions and put everything in as default and when i go to restart the xserver it still gives the same error.  Maybe someone can help me with this issue instead.  ive also tried a command "sudo dpkg-reconfigure -phigh....." and this was also unsuccessful.  i really dont know what else i can do, can anyone give me a lead?:confused:

---

