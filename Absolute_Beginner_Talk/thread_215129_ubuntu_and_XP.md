---
title: "ubuntu and XP"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Typo on 2006-07-13
Hello guys,

Yep, I'm a linux nub and want to learn more about it. I feel it will be great to start off with ubuntu. I have used linux before (fedora core 5 & knoppix live cd), Basically here is my situation:

I will begin to tell you about my pc spec:

Windows XP
Pentium 4 HT 3.8ghz
200GB HDD
200GB HDD (second hdd)
ATI Radeon x700 pci express
card readers (dont use)
tv tuner (dont use)
1 gb ram

Ok so now you know my spec. What I want to do is keep XP for gaming and so on. So what I need is to install ubuntu on my second hard disk. Basically how do I go about this? Also... how would I "switch hdd" for boot. So I can boot in xp or boot in ubuntu...

I am visual person so any visual tutorials would be handy! If you can help.. GREAT.. thanks

---

### Post by neilp85 on 2006-07-13
I don't know about any visual tutorials but the graphical installer for dapper is very easy to follow. Just pop in the live CD and double click install. When you come to step 5 that should handle partitioning and you should have an option to erase your second hdd and use it for you ubuntu install.

---

### Post by aysiu on 2006-07-13
Here's a visual tutorial:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by Typo on 2006-07-13
Thanks, I will read tutorial and get back to you if I have any problems...

---

### Post by linuksamiko on 2006-07-13
ok, this is how it works:

it is no prob to install two (or more) Operating Systems (OS) at the same time. It is even possible to install them on one Harddisk but it is of course a little nicer if you have one Harddisk for one OS.

When ever you installed your system you can choose between the OSs when your computer boots. This is called the grub bootloader.

If you want to know how smooth the installation will go you should take a look at this:
[http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=4&title=ubuntu+6.06+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=4&title=ubuntu+6.06+screenshots)

This will show you how Ubuntu looks like from the first CD-Boot until the installation is finished.

---

### Post by Typo on 2006-07-13
The tutorial is about partitioning how do I just install on a blank HDD :/

---

### Post by aysiu on 2006-07-13
The tutorial is about everything--wiping the whole hard drive, repartitioning to make two partitions, installing to existing partitions.

What you want is installing to existing partitions. It's the same procedure to have two partitions as it is to have two separate hard drives.

The only difference being that two partitions are likely to be called /dev/hda1 and /dev/hda2, and two hard drives are probably called /dev/hda1 and /dev/hdb1. Same principles apply.

---

### Post by Typo on 2006-07-13
Ok, so when all is installed etc etc... "grub" will load up and ask if which hdd I want to boot from? or does it automatically boot to linux?

Sorry but I am paranoid of loosing windows... lol

---

### Post by aysiu on 2006-07-13
If Grub is installed to the MBR--which the Desktop CD does without asking you--then, yes, about 90% of the time, Windows will automatically be added to the boot menu.

Then, when you boot up your computer, you'll get a choice of whether you want to boot Windows or Ubuntu. The default will be Ubuntu, and you'll get ten seconds to decide which to boot. If you want to make Windows the default or change the timeout from ten seconds to something else, that can be done post-install.

In the 10% of cases where Windows doesn't automatically get added to the boot menu, it's usually a trivial matter of adding a few lines to the /boot/grub/menu.lst file. Trust me--it's a lot easier than trying to add Ubuntu to Windows' boot loader.

---

### Post by Typo on 2006-07-13
ok thanks for the help apreciate it, I will study it in more detail while I am waiting for ubuntu to download :)

---

### Post by gmatt on 2006-07-13
> **Typo said:**
> Hello guys,

Yep, I'm a linux nub and want to learn more about it. I feel it will be great to start off with ubuntu. I have used linux before (fedora core 5 & knoppix live cd), Basically here is my situation:

I will begin to tell you about my pc spec:

Windows XP
Pentium 4 HT 3.8ghz
200GB HDD
200GB HDD (second hdd)
**ATI Radeon x700 pci express**
card readers (dont use)
tv tuner (dont use)
1 gb ram

Ok so now you know my spec. What I want to do is keep XP for gaming and so on. So what I need is to install ubuntu on my second hard disk. Basically how do I go about this? Also... how would I "switch hdd" for boot. So I can boot in xp or boot in ubuntu...

I am visual person so any visual tutorials would be handy! If you can help.. GREAT.. thanks


It sounds like your computer is quite powerful and I guess you enjoy to play games and such. ATI drivers on linux have always been subpar to Nvidia drivers and even though a very strong ATI card might perform well under windows with ATI windows-based drivers, the drivers ATI gives for its linux users are pretty aweful. If you plan to play games on linux I foremost recommend you strongly consider purchasing a Nvidia card.

---

### Post by Typo on 2006-07-13
I don't plan on playing games on linux, this is the main reason why I want to keep windows :) I plan to learn on linux and understand how it all works etc etc...

---

### Post by aysiu on 2006-07-13
My advice--take it slow.

1. While Ubuntu is downloading, back up all your important Windows files. Make sure you have a Windows restore disk of some kind and could get Windows up and running in case you accidentally choose the wrong drive to reformat (it's happened before).

2. Before installing Ubuntu, play around with the live CD for a bit. Get comfortable with the new interface. Make sure that the sound works, the internet works, the screen resolution is correct. Try to solve those problems with the live CD *before* you commit to an installation. I'd play around with the live CD for at least a week, if not two.

3. Once you're confident that you have nothing to lose (i.e., all your files are backed up) and that Ubuntu will work on your computer (or you know how to fix the things that don't work), go ahead and install it.

---

### Post by Typo on 2006-07-13
ok, the interface is the same as that of fedora core? I used terminal a little on that to install windows fonts & make mp3 work..

---

### Post by aysiu on 2006-07-13
I'm sorry. I'm an idiot. I re-read your first post--you've already used Knoppix and Fedora. In that case, just go ahead and dive right in.

You don't need to take it slow.

---

### Post by Typo on 2006-07-13
After reading the tutorial you gave earlier.. as long as I don't click erase HD1 etc etc etc I will be ok... I am quietly confident now. Thanks for shedding light on all this I was curious before I install ubuntu..

I will be back saying it all works great and windows does aswell pretty soon ;)

---

### Post by Sonofmoog on 2006-07-13
> **aysiu said:**
> 
In the 10% of cases where Windows doesn't automatically get added to the boot menu, it's usually a trivial matter of adding a few lines to the /boot/grub/menu.lst file. Trust me--it's a lot easier than trying to add Ubuntu to Windows' boot loader.

Adding any version of Linux to the Windows bootloader is a piece of cake.  The only time it's hard is when the entire FS is NTFS, and there's no floppy drive, but for example purposes we'll assume a floppy drive A:

1) Open a console, and issue the command

```
sudo dd if=dev/hda2 of=/dev/fd0/Ubuntu bs=512 count=1
```

This copies the bootsector of the Linux partition to a floppy disk. Substitute the device number of your Linux partition in the if= parameter.  
2) Start Windows
3) Copy the bootsector file, Ubuntu, to the root directory of drive C:
5) Open boot.ini in notepad, and add this stanza to the file on the last line.

```
C:\Ubuntu="Ubuntu"
```
4) Reboot 
5) At Grub, choose Windows
6) If everything went according to plan, the next thing you'll see is the Windows multi-boot menu.  Select Windows and Windows will load; select Ubuntu and you'll see Grub again.

---

### Post by aysiu on 2006-07-13
How is that easier than just installing Grub to the MBR (which the desktop CD does without asking you) and having Windows added to the dual boot automatically?

---

### Post by Sonofmoog on 2006-07-13
> **aysiu said:**
> How is that easier than just installing Grub to the MBR (which the desktop CD does without asking you) and having Windows added to the dual boot automatically?

I never claimed it was.  I was responding to an earlier quote of yours that implies that booting Linux from Windows is harder than booting Windows from Linux.  Specifically, you said:

> Trust me--it's a lot easier than trying to add Ubuntu to Windows' boot loader.

I don't think adding Ubuntu to Windows boot loader is especially hard.  It is the way I boot - not only Ubuntu, but PC Linux, and even Windows 98, and it has worked to this point without a hitch ..

---

### Post by aysiu on 2006-07-13
Easier is a relative term, and, yes, I do believe it's easier to do nothing and have it set up automatically than to do that *dd* command and manually edit the boot.ini file.

---

