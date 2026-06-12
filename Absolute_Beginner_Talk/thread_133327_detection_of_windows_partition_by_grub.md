---
title: "detection of windows partition by grub"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by alek on 2006-02-20
Hello! :)

I had Ubuntu Linux up until couple of days ago, when I decided to replace it with Fedora Core 4 (please don't kill me!:) :) What it was is that I needed some IDEs for C++, but after a painstaking effort to download numerous .tar files, and unpacking one after the other, always discovering that I am missing some, I just decided to get Fedora...

The problem is this: I was running a windows partition and a linux partition on my computer. After installing fedora, I reinstalled grub bootloader (I KNOW! What a stupid thing... should have just kept the initial grub bootloader). During the installation process, I was asked to select another partition (if applicable) that contains an operating system, which I did. However, even though my Linux runs perfectly, I cannot start my windows partition. After I select windows as my startup option, it just sits there, and does nothing. Apparently, it does not "see" the executable files it needs to. It just asks to press any key to return to the previous window of the bootloader...

An even greater problem is this: my windows partition contains some 20 pages worth of my project plan (work distributions, Gantt charts) that I need for my group project at university. It would save me HOURS to time if I could get my windows to work... and get all my files back...

ANY help is GREATLY appreciated... As I am a Linux newbie, please reply in Standard English (i.e. not Computerese... as chances are that I won't understand :)

Thank you,
Alek

---

### Post by don cole on 2006-02-20
I just went through the same thing.

as lot of people on this list my not like my solution because it does not deal with GRUB.

Make a bootable floppy with GRUB.

[http://www.ranish.com/part/](http://www.ranish.com/part/)

Down load 2.37 and make a back up disk of your partitions.
Put it away when done.

Download 2.44 and make a bootable disk.
Use that disk to boot the partition manager.
Under masterboot record install the "compact boot manager"

Restart your computer using the boot manager to start the partiion your window 2000 is on.

If all this works you may need your floppy to restart ubuntu.
Then you can reinstall Grub in the partition where ubuntu lays.

Hope this helps,

Don Cole

---

### Post by lha on 2006-02-20
[QUOTE=alek]Hello! :)

I had Ubuntu Linux up until couple of days ago, when I decided to replace it with Fedora Core 4 (please don't kill me!:) :) What it was is that I needed some IDEs for C++, but after a painstaking effort to download numerous .tar files, and unpacking one after the other, always discovering that I am missing some, I just decided to get Fedora...

The problem is this: I was running a windows partition and a linux partition on my computer. After installing fedora, I reinstalled grub bootloader (I KNOW! What a stupid thing... should have just kept the initial grub bootloader). During the installation process, I was asked to select another partition (if applicable) that contains an operating system, which I did. However, even though my Linux runs perfectly, I cannot start my windows partition. After I select windows as my startup option, it just sits there, and does nothing. Apparently, it does not "see" the executable files it needs to. It just asks to press any key to return to the previous window of the bootloader...

An even greater problem is this: my windows partition contains some 20 pages worth of my project plan (work distributions, Gantt charts) that I need for my group project at university. It would save me HOURS to time if I could get my windows to work... and get all my files back...

ANY help is GREATLY appreciated... As I am a Linux newbie, please reply in Standard English (i.e. not Computerese... as chances are that I won't understand :)

Thank you,
Alek[/QUOTE]
I consider reinstalling grub was the right thing to do. So, don't worry. :) Post the contents of your menu.lst here.and list of your partitions.
```
cat /boot/grub/menu.lst
sudo fdisk -l
```
(Those two commands should be entered into a terminal. Copy&paste the results here.)

(Alek uses Fedora and asks questions in Ubuntuforums. :confused: )

---

### Post by don cole on 2006-02-20
I've been thinking about your problem.
Was Partition 1 your Windows Partition?
If it was you probably messsed up the bootable part of that partition.  but not the data. So DO NOT formatt that partition.

What you need is a third party partition manager Pasrtition Magic or some thing like that if you have it. I recomended Ranish Partition Manager because it's Free.

Maybe you can do it with your Linux software.

A simple solution: set a side another partition 2GB is plenty and install 
Windows in that partition. From there you sould be able to access you data
from the old windows partition.

Don Cole

---

### Post by Bartender on 2006-02-20
alek -
I don't know if you're being pulled in too many different directions here, but it looks like there are Windows-based solutions also.  Since the Windows partition is the one you need to get at, maybe that would be the most straightforward path?
Excerpted from 'Linux in a Nutshell':

"When you install the boot loader on the MBR, it replaces the MS-DOS boot loader, or any other boot loader that may be there, such as the Windows NT loader. (Used in NT/2000/XP) If you have problems w/ your installation or you simply want to restore the original boot loader, you can do one of the following:

-If you have the capability, boot to DOS & run the **fdisk** command with a special option that rebuilds the MBR:      

C:> fdisk /mbr

-For W2K & XP, which don't have an **fdisk** cmd, boot from the Windows CD (or the Windows boot floppies).  When you see the "Welcome to Setup", press R (for repair) and, in W2K, then press C.  Select your Windows install from the numbered list, enter admin password at the prompt.  Enter the command **fixmbr** at the command-line prompt, confirm Y.  After mbr's restored, type **exit** to reboot."

Hope that helps

---

### Post by alek on 2006-02-20
In reply to Iha:
As per your instructions, I have executed the above-mentioned commands, and I have received this:
[root@localhost ~]# cat /boot/grub/menu.lst
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
hiddenmenu
password --md5 $1$GqD5vaM/$ZLieq7OZ84o7Ve3g/g9OU0
title Fedora Core (2.6.11-1.1369_FC4)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.11-1.1369_FC4 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.11-1.1369_FC4.img
title windows xp
        rootnoverify (hd0,4)
        chainloader +1


and also, for the second command:
[root@localhost ~]# fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        2017    16137292+  83  Linux
/dev/sda3            4472        4863     3148740   db  CP/M / CTOS / ...
/dev/sda4            2018        4471    19711755    5  Extended
/dev/sda5   *        2018        4367    18876343+  83  Linux
/dev/sda6            4368        4471      835348+  82  Linux swap / Solaris
Partition table entries are not in disk order



I hope that helps :) The reason I have so many partitions on my hard drive is because I have a laptop I purchased from Dell, and so straightaway it came with one main partition, and about a couple little ones for backup, Dell media centre and so on... the two big partitions were made by me with ubuntu out of one big one.

The only thing I do not understand is how come the partition /dev/sda5 says "Linux"... unless I have accidentally installed linux on my windows xp partition... which is unlikely because I distinctly remember my windows partition being larger than my linux one... I used windows more, and that is why I set it to be larger.

And yes... I realize that I should not be asking questions in Ubuntu forums as I run fedora... however, after spending lots of time googling my problem, and having had ubuntu just before fedora, I did  not think it was a problem :)

---

### Post by alek on 2006-02-20
in reply to don cole:

As per your second message, I do not believe that simply installing windows in one partition will work, as my windows xp behaves as if it does not see any other partitions. The first time I had one windows xp partition, one ubuntu, and a couple of dell partitions, windows could only see the one in which it was in, being blissfully unaware of any other partitions.

I am still working on your first message (making a bootable GRUB floppy) :) I will inform you  of the results by tonight (Eastern Standard Time), as I have to leave right now.

Thanks,
Alek

---

### Post by alek on 2006-02-20
In response to Bartender:

In order to execute your solution, I will have to order a CD from Dell... the thing is, when I got my laptop, windows xp was installed on it prior to delivery... I do not actually possess a windows xp CD, or anything related to my operating system.

Is there any way I can download the contents of an MSDOS bootable floppy?

Thanks,
Alek

P.S. I just remembered, having a laptop, I do not have a laptop floppy drive :( but not to worry... I can borrow it from a friend.

---

### Post by lha on 2006-02-20
[QUOTE=alek]I hope that helps :) The reason I have so many partitions on my hard drive is because I have a laptop I purchased from Dell, and so straightaway it came with one main partition, and about a couple little ones for backup, Dell media centre and so on... the two big partitions were made by me with ubuntu out of one big one.

The only thing I do not understand is how come the partition /dev/sda5 says "Linux"... unless I have accidentally installed linux on my windows xp partition... which is unlikely because I distinctly remember my windows partition being larger than my linux one... I used windows more, and that is why I set it to be larger.[/QUOTE]

Yep, this helps. It seems that you have overwritten Windows with Fedora. Your menu.lst shows you boot Fedora from hda2. Based on your partition table, I believe Ubuntu was installed on hda5. You can confirm this if you mount hda5. If it contains Ubuntu, you have installed to wrong partition.

---

### Post by alek on 2006-02-20
So... I made so much fuss about a thing that does not seem to be in existence, then? All this time it simply was not there...

Thank you for pointing out my stupidity :) I will just have to reinstall windows xp from scratch... and better to it fast...

I wish I could be justifiably angry at Linux... but then, as they say in programming, "Garbage in, garbage out." It was all my fault from the very beginning...

Thanks for your help,
Alek

---

### Post by don cole on 2006-02-21
I had one windows xp partition, one ubuntu, and a couple of dell partitions, WINDOWS could only see the one in which it was in, being blissfully unaware of any other partitions.

The key word here is Windows. This is why I say you need a third party Partition Manager (Not Windows or Ubuntu) such as Ranish Partition Manager.  Which is free.

[http://www.ranish.com/part/](http://www.ranish.com/part/)

The purpose of the GRUB boot disk is so you can reboot ubuntu from the floppy if you messup you MBR.

The purpose of making 2.37 floppy is to back up you current MBR and partition scheme. They will tell you how to do it. You'll have to do this from Linux if that's the only way you can get on line.

Boot version 2.44 from a bootable floppy (they will show you how to do that).

Now look at your current partition scheme. Maybe you have an extra partition you don't know about. Or maybe you will have to create another partition. If you want I could mail you the RPM floppies.

You put in the floppy in restart you computer and get an A:_
Type in "part" the partition manager starts running in DOS. Windows or Ubuntu doesn't know any thing about it.

Don Cole

---

