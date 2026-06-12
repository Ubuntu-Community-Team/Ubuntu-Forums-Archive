---
title: "grub - how do I edit menu.lst?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by andyfonforum on 2006-12-02
Grub boot loader does not list my windows 98se bootable partitions in its menu.  (the menu that comes up when you press Esc) Can anyone tell me how to edit the 'menu.lst' file in /boot/grub/ successfully to include the option to boot into my Windows 98se operating system?

Can anyone also tell me how to make this boot menu come onscreen and stay there until a boot option is selelcted?

Also I would like to password protect my pc at this point, so if anyone knows how to do this I would be grateful.

Used to use BootMagic in windows to do these things.

My bootable windows partitions (I have two) are on hda1 and hda2, my ubuntu partition is hda3 and the swap file is hda4.  I have all my windows data files in hda5 i.e. .doc and .xls files etc..

I am very wary of editing the menu.lst file as if I get it wrong I might then not be able to boot into any operating system at all and will be in the faeces.

I refer to my previous Thread "Grub - Problem" posted three or so hours ago, and thanks for the input from those guys.
I think I did not expain myself very well for which I apologise - have had a nose around the forum and the files on my computer I begin to understand the question I should ask, so I have put this new thread in the forum -  - - andy

---

### Post by bulldog on 2006-12-02
To go to your menu.lst ```
gksudo gedit /boot/grub/menu.lst
```

Put the outcome of ```
cat /boot/grub/menu.lst
``` on the forum so we can have a look.
Also the outcome of```
sudo fdisk -l  [l as like]
``` would be appreciated.

---

### Post by andyfonforum on 2006-12-02
I put the text of menu.lst into this message but I think it was too big because errors came up saying I had too many images in my reply - so I took the text of this file out.

This is the ouput of the commands you gave -

typing code  - cat/boot/grub/menu.lst  = No such file or directory
same happens if I leave a gap between 'cat' and '/'


andyub@a5:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             440         785     2779245   1b  Hidden W95 FAT32
/dev/hda2             786        1318     4281322+   c  W95 FAT32 (LBA)
/dev/hda3   *        1319        2248     7470225   83  Linux
/dev/hda4            2249        3648    11245500    f  W95 Ext'd (LBA)
/dev/hda5            2293        2568     2216938+  1b  Hidden W95 FAT32
/dev/hda6            2569        3352     6297448+  1b  Hidden W95 FAT32
/dev/hda7            3353        3519     1341396   1b  Hidden W95 FAT32
/dev/hda8            3520        3648     1036161   1b  Hidden W95 FAT32
/dev/hda9            2249        2292      353367   82  Linux swap / Solaris

Partition table entries are not in disk order

How about that - my swap file is hda9

I entered these commands in the Terminal - I don't know if this is the right place to do this.  I am completely clueless about this sytem.  
appreciate your help - regards andy

---

### Post by bulldog on 2006-12-02
Are you on the live cd or have you booted from hard disk?

If you use the live cd you have to mount your ubuntu install first.

What is the use of all the hidden partitions?

---

### Post by andyfonforum on 2006-12-02
hi
i am booting from the hard disk

the hidden partitions (hda5,6,7,8) are full of my windows data files and I hid them before I loaded ubuntu in the vague hope that if I got things wrong with the partitioning software in ubuntu it would not over write the data.  I know this is silly because what usually causes data loss is loss of the MBR or the setting of existing partitions with the wrong start and end numbers.  This once happened to me about four years ago and I had to get special software from R-studio to recover all my 'overwritten' files.  They weren't over written mostly the FAT32 Table was just destroyed.

one of the partitions holds program files that are not essential to be in the C drive but are necessary.  The C drive is also backed up in hda1.

When you push Windows to do a lots of different things with legacy software, xp software that MS allows to be loaded on top of Window98se, and software that was/is current to Windows98se, Windows gets a bit flaky to say the least.  (I refuse to spend atleast £500 or more upgrading)

I have reacted to this with multiple backups, repeated copies of whole drives, and the most enormous catalogue of 'cleaning, registry maintaining, disk maintainig, security maintaining, etc, etc, software.

There is more mantenance software on my machine than programs that do things that are productive.  I want out, but I need to be able to boot into Windows98 for another year. regards andy

---

### Post by andyfonforum on 2006-12-03
hi
I have deleted Ubuntu from my hard disk as in the set up of the partitions it had over written the MBR incorrectly - this I imagine is because I did not tell it all the correct information when I allowed it to partition the drive - 

The problem I have with this is that the dapper drake disk that I have has not instruction on this part of the set up that are at all help for a newbie and this is the one place in the install when you need to be absolutely correct.

The install process that I have makes it all look as though it is automatic - the partioner did not automatically detect my windows partitions correctly and the MBR was damaged.

I have now corrected this in windows which is booting just fine.

I think GRUB needs to tell us newbies a few things in detail - specifically how to manually set up the partitions defining mount points etc, and this applied to the windows partitions as well as Ubuntu.

I could have lost all my data again as happened four years ago - 

I am basiscally disappointed because I wanted to run Ububntu and probably won't because I have not way of protecting my windows set up because it is all on one drive. I don't think this should be like this.  There are loads of 'similar' messages on the forum to mine - it can all be Windows fault even if we all wish it was.    Will try again later, I apreciate and thank you for your help - andy

---

### Post by bulldog on 2006-12-03
Sorry to hear you give up on Linux.
There's a load of information about GRUB and fstab and how you have to partition your drives to get a usable Ubuntu.

Most people walk into Ubuntu with a live cd and they think,well pop in the cd and all will go flawlessly.
This is truth if you have a hard disk which is empty!!
But if there comes a windows install and a lot of data partitions you have to think twice what you are going to do.

First thing is,if you have multiple hard disks that is,to avoid installing ubuntu and windows on the same disk.
Try to keep your windows and stuff on one disk and install Ubuntu on the other with a partition for shared data if you want.

If you have just one disk with a lot of valuable data,don't install ubuntu on that disk without making backups.
This is one of the first things you have learned when you got busy with a computer.
**Make always a reliable backup,especially when you go messing with partitioning and resizing**

But unfortunately this is forgotten by most people,till things go wrong.

---

### Post by wxnker on 2007-02-20
How sad Andy* left the wonderful world of Ubuntu because of his problems with Grub.
Right now I'm typing this WHILE installing "Feisty Herd 4" on the same machine. Gotta love Linux.

There's one thing I'd like to add to this subject though because **I installed Ubuntu and Windows Vista on the same harddisk with 3 partitions (Ubuntu, XP & Linux swap) with no problems and without touching a command line** (I had never used Linux before at the time so I used the informations in this great forum). 
[U]
Installing Grub but not on the MBR:[/U]
From my experience it can be a good idea NOT to install Grub on the MBR (Master Boot Record). This can normally be changed right after the "partition setup" during the install of Ubuntu by choosing the button "ADVANCED" just before the installation starts copying files.

I'm no expert but I use this method because of the possibility to install other OS's like Windows later on. As far as I know Windows will (always) write it's boot information on the MBR and thereby overwrite the Ubuntu Grub file if it's installed on the MBR.
This may be a minor detail but as I see it, a convenient one.

If I want to add an Windows OS I can do this without changing the Ubuntu Grub and when Windows is installed I just start Google and download a small free program **[COLOR="Red"](EasyBCD)[/COLOR]** that can change the boot up Grub settings from a GUI within Windows Vista.

I think this information may be convenient for the novice Linux user and not as scary as using a command line to edit the Grub menu.lst.

The only thing to remember is to know how Grub list disks. (0 = first disk (hda) 1= second disk etc (hdb).) (0,0 first disk, first partition (hda1) etc.). Correct me if I'm wrong. Anyway, there's plenty of information on this on the www.

e.g. I have Ubuntu Edgy on the first harddisk and the first partition so I installed grub to (0,0) and not the default choice (0) which would be the MBR.

I hope this could be a suggestion for new users. 

_With Windows already installed:_
I have not tried to install Ubuntu on a system with Windows already installed, but I would think that by doing it this way, the Windows boot should be left intact and then it's pretty easy to boot into Windows, download the tool for Windows, do the grub settings without using any code and get the bootmanager on the next reboot.

[U]
Wtih an Empty system/harddisk:[/U]
If you, like I did, want to setup an Ubuntu and Windows system from scratch with an empty harddisk, I have had success with doing it this way. 

1. Install Ubuntu but choose not to install Grub on the MBR
2. Install Windows
3. Boot into Windows and download the tool for Windows. 
4. Install the tool and show it your Linux partition where the Grub file is.
5. Reboot and choose which OS to boot.

This might be posted elsewhere and this is merely the way I did it, so it's just a suggestion on how to do it the easy way.

Regards Wxnker

[COLOR="Red"][B]EDIT: The tool is called EasyBSD. I do not know if it works with other versions of Windows than Vista, but the name BSD indicates that it is merely a tool for Windows Vista (BSD being the "Boot Configuration Data" in Windows Vista), but If the tool does not work with XP (I don't know as I'm running a Windows FREE system *"Free at last..."*) then I guess there are similar tools for Windows XP etc.

For more information and to download the tool:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)[/B][/COLOR]

---

