---
title: "Dual Boot Help: Windows isn't option on startup"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by bunnicula on 2006-07-05
I'm a complete Linux newbie. I have never used Linux or command lines before, so I am probably going to need some detailed instructions...

I just set up a dual boot with Windows XP and Ubuntu 6.06 on my Compaq Presario 2100 notebook (40 GiB HD, 512 RAM). Windows was already installed, so I backed up my documents, resized the partition and created two new partitions out of the free space.

Here are the three partitions:

Partition 1: 
Device: /dev/hda1
Filesystem: Windows NTFS
Access Path: /media/hda1 (this was the default)
Size: 17.23 GiB

Partition 2:
Device: /dev/hda2
Filesystem: Extended3 (ex3)
Access Path: /
Size: 19.53

Swap partition:
Device: /dev/hda3
Filesystem: Memory swap
Size: 509

I then installed Ubuntu on the second partition. The install went well and the computer now boots into Ubuntu without any problems (well, I still need to manually set up my wireless, but that's another issue). 

I am having problems, however, booting into Windows. When I press ESC during the boot up (to access the Grub menu), I am only given three options (Ubuntu, Ubuntu safe mode [or restore - I can't remember the wording] and a Ubuntu mem test). 

How can I make it so that Windows is an option in the Grub menu? While in Ubuntu, I can see the Windows partition and all of my files, so I know that it is there...

---

### Post by confused57 on 2006-07-05
You'll need to open a terminal:Applications---Accessories---Terminal

Copy & paste these lines one at a time, press enter after each line:
```
sudo fdisk -l
cat /etc/fstab
```

This will tell you exactly what your partition table looks like.
If your Windows partition is hda1, then you'll need to add the entry to your
/boot/grub/menu.lst file, which will add the entry to grub and give you an option to boot Windows.
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
The first command changes directory to grub, the 2nd command creates a backup of your menu.lst file, and the 3rd command opens the menu.lst file in the text editor gedit.
If you'll notice, there is an example of what a Windows entry should be and if your Windows partition is hda1, it should look like the entry listed as an example.
Add an entry for Windows, following the example(without the # in front of each line), at the bottom of the file, then when you bootup, there should be a Windows entry at the bottom.  You can put whatever you want on the title line, e.g. Windows XP, Windows XP Pro, etc.

You might also want to add a # in front of the hiddenmenu option and change the timeout to however many seconds you want the grub menu to display.

If you have any problems or questions, don't hesitate to ask.

The Ubuntu installer usually automatically adds the Windows entry to grub, if you chose to install grub to the mbr during installation...don't know why it didn't.

---

### Post by bunnicula on 2006-07-05
It didn't ask me anything about grub (or maybe it did and I wasn't in the room)...

Here's what it said about my partitions:

> 
 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2249    18065061    7  HPFS/NTFS
/dev/hda2            2250        4799    20482875   83  Linux
/dev/hda3            4800        4864      522112+  82  Linux swap / Solaris


> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


And here's what the examples look like:

> 
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#


Do I just need to copy the first four lines (title, root, makeactive, chainloader)? How do I enter the title for Windows XP? What should I enter as the root (or should I just copy the example)? Also, where exactly do I copy it? At the end menu.lst file? Does it matter if it comes before or after Ubuntu?


Thanks for all your help.

---

### Post by confused57 on 2006-07-05
[QUOTE=bunnicula]
Do I just need to copy the first four lines (title, root, makeactive, chainloader)? How do I enter the title for Windows XP? What should I enter as the root (or should I just copy the example)? Also, where exactly do I copy it? At the end menu.lst file? Does it matter if it comes before or after Ubuntu?

Thanks for all your help.[/QUOTE]

You'll just need the Windows entry at the very end of your menu.lst file:
```
 title Windows XP
 root   (hd0,0)
 makeactive
 chainloader +1
```

This should work for Windows on hda1, which in grub is designated (hd0,0).
See if this works...if it does you can move the entry later, above the line:
###BEGIN AUTOMAGIC KERNEL
that way Windows would boot by default, unless you scrolled down & chose Ubuntu.

---

### Post by bunnicula on 2006-07-05
Thanks for the help. It worked like a charm - I booted in and out of windows without any problems. 

Now I am going to go read up on how to do other things.

---

### Post by confused57 on 2006-07-05
[QUOTE=bunnicula]Thanks for the help. It worked like a charm - I booted in and out of windows without any problems. 

Now I am going to go read up on how to do other things.[/QUOTE]

Great, I'm glad it worked...I knew it should, but you never know.  Welcome to Ubuntu and dualbooting,  I still need my Windows XP, also...but Ubuntu sure is a lot of fun.

---

