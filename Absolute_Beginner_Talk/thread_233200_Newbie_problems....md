---
title: "Newbie problems..."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by dicchicora on 2006-08-09
Ok, I'm new to, not just Ubuntu, but Linux in general.  I've decided to give Linux a try and heard Ubuntu would be the best choice for a newbie.  However, I've run into a couple problems.

1. The live cd will not work on my machine.  It will go through the loading of all the files, but when it starts the OS, I get a message from my monitor saying "Mode Not Supported", and then I just get a black screen.

2. So, I download the alternate cd and just go ahead and install Ubuntu.  It seems to work, except, I can't get grub to load, so I can't choose Ubuntu.  I have a feeling it's because I have an IDE HD and a SATA HD.  The SATA HD is my main disk and has Windows XP and my backup partition on it.  The IDE HD is my secondary disk for testing (i.e. Ubuntu or Windows Vista).  So, Unbuntu is installing grub on the IDE HD, but I'm thinking grub needs to be installed on the SATA HD.  

Any and all help on how to get Ubuntu up and running would be great!  I'm really interested and anxious to try it out.  Thanks in advance.

System specs:
AMD64 2000+
512MB Ram
Disk #1 - Maxtor - SATA (WindowsXP, and backup files)
Disk #2 - Wester Digital - IDE (Ubuntu installed)
ATI 9600 All-in-Wonder
Creative SB Audigy 2 NX
19" LCD by MAG

---

### Post by Lord Canti on 2006-08-09
I can tell you that the "Mode not Supported" means that your monitor can't show at the reslution. Too high I think, I don't think it would be too low.

---

### Post by Dr. Nick on 2006-08-09
For the mode not supported eror, boot the live cd and choose one of the other graphical modes before it boots, their should be something like "safe graphic mode" that may work.

I have no expierence with sata though

---

### Post by confused57 on 2006-08-09
Since you have 2 hard drives, you might want to consider this as an option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If grub was installed to your IDE drive, you could set your system to boot first from it, then add the Windows entry mentioned in the link.  I assume you have no trouble booting into Windows from your SATA drive, i.e. grub was not installed to that drive.  I also don't have any experience with SATA drives, other than what I've read on the forums...

If you are able to access the grub menu, you might want to boot up in recovery mode, which will get you to a console, where you can reconfigure your xserver & select the resolutions for your monitor:
```
sudo dpkg-reconfigure xserver-xorg
```
Here's an excellent tutorial for xserver reconfiguration:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

You might want to find out your Monitor specs, such as refresh rates, maximum resolution, etc.

---

### Post by scxtt on 2006-08-09
it's my understanding that grub will be installed to IDE (not matter what) if it's present ... i've had it installed on my SATA disks, but as soon as i put an IDE drive in and reinstalled Kubuntu, BAM, grub was on the IDE disk ... no problem, i just use the IDE HDD (that doesn't have an OS installed on it) as the boot disk and boot Kubuntu from the SATA drive ...

the **root[color=white]__________[/color](hd1,0)** rules still apply even if it's IDE / SATA ...

---

