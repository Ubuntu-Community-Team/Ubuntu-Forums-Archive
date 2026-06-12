---
title: "Problems with dualboot&amp;grub"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-12
Ok, I runned only linux and wanted to make a dualboot with XP for photoshop, ipod and some games..

When I installed windows I couldnt boot linux anymore.. then I found out that I need to install grub, I did it from liveCD, but then I couldnt boot windows, on grubs menu there was only ubuntu, ubuntu safe mod and memory test :confused: 

Now I needed to access windows for a moment, I re-formated windows partition and installed XP and when I want to install grub again it says
> ubuntu@ubuntu:~$ sudo grub-install hd0,0
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


What Im doing wrong? can anyone guide me to make a dualboot with success?

---

### Post by richbarna on 2006-06-12
I've had a few GRUB problems too,
Try this guide :)
[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by cotcot on 2006-06-12
First of all installing Windows after Linux is not the easiest way. Installation guides always suggest the opposite. When you install windows after linux windows just replaces the bootloader installed by linux to its own. So no linux boot any more.
There is a trick to avoid this. It is explained in [http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html")

This trick is to make think windows that it is installed on the first partition although it is not :

title Windows 98
	map (hd0,0) (hd0,2)
	map (hd0,2) (hd0,0)
	rootnoverify (hd0,2)
	chainloader +1

---

### Post by J-Gaming on 2006-06-12
[QUOTE=richbarna]I've had a few GRUB problems too,
Try this guide :)
[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")[/QUOTE]
Thats for restoring.. I think, but I need to completely start from over..

[QUOTE=cotcot]First of all installing Windows after Linux is not the easiest way. Installation guides always suggest the opposite. When you install windows after linux windows just replaces the bootloader installed by linux to its own. So no linux boot any more.
There is a trick to avoid this. It is explained in [http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html")

This trick is to make think windows that it is installed on the first partition although it is not :

title Windows 98
	map (hd0,0) (hd0,2)
	map (hd0,2) (hd0,0)
	rootnoverify (hd0,2)
	chainloader +1[/QUOTE]
I have XP not 9x

---

### Post by cotcot on 2006-06-12
Is the same trick.

This is the explanation come from 'grub manual' :

4.2.6 DOS/Windows
GRUB cannot boot DOS or Windows directly, so you must chain-load them (see Chain-loading). However, their boot loaders have some critical deficiencies, so it may not work to just chain-load them. To overcome the problems, GRUB provides you with two helper functions. 

If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see map), like this: 

     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)

---

### Post by richbarna on 2006-06-12
Ok, Normal situation,
1. install windows
2. install linux (everything appears on Grub)

---

### Post by J-Gaming on 2006-06-12
> ubuntu@ubuntu:~$ grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.


> 
    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found


in boot/grub directory I only have device.map file.. 

It seems like my grub is really messed up..

I mean.. none of grub command works

---

### Post by richbarna on 2006-06-12
This guide tells you how to add oS's to the Grub menu :-
[http://os.newsforge.com/article.pl?sid=04/12/21/1852209&from=rss]("http://os.newsforge.com/article.pl?sid=04/12/21/1852209&from=rss")
This guide tells you how to Dual boot anything :-
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Sorry I can't give more specific help, 
But I think the links will give you all the information you need ;)

Good Luck !!

---

### Post by cotcot on 2006-06-25
There is something wrong with dapper. In breezy it is no problem.

---

