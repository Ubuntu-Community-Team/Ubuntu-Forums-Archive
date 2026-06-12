---
title: "Unable to boot Ubuntu install CD's on Pismo Powerbook G3 500mhz"
date: 2007-09-16
forum: Apple PPC Users
---

### Post by rjt1000 on 2007-09-16
Hi All,

I am a long time Mac user, but brand new to Ubuntu. 

I am trying to install Ubuntu on my trusty old PowerBook G3 500 mhz (Pismo) with 768 mb RAM and a 20GB internal hard drive. The OEM DVD/CD reader died several years ago and I replaced it with a combo drive off eBay, model: "HL-DT-ST CD-RW/DVD-ROM GCC-4240N" which started its life in a windows PC but has always worked fine in my Pismo (installed in the original media bay sled) and has been used repeatedly for reading, writing and for booting OS 9 and OS X disks without fail.

I would like to be able to dual boot, Ubuntu and OS X 10.4.10. I used OS X disk utility to partition the drive into 2 roughly 9.2 gb partitions of type Mac OS extended, and I installed OS X 10.4.10 onto the second of the 2 partitions.

Because of the difficulties detailed below I wound up downloading each of the following 4 images and burning each of them to CD: Ubuntu 7.04 PPC desktop live, Ubuntu 7.04 PPC desktop alternate install, Ubuntu 6.06 PPC desktop live and Ubuntu 6.06 PPC desktop alternate install.

I know that the CD's are good, because I can use them to boot my PowerBook G4 12 inch, but unfortunately that is NOT where I want to install and play with linux.

BTW, I can use OS 9 and OS X installation disks to boot the Pismo from the CD drive without problem.

However, I have tried booting the Pismo from each of the above 4 Ubuntu CD's but I cannot get any one of them to boot the machine. I have tried: 
-holding down the option key, selecting the Penguin icon but after hearing the CD spin up, it stops, nothing happens and the screen stays black until I force restart
-holding down the C key, but after hearing the CD spin up and down, the Pismo starts up with the OS X on the hard drive
-holding down option-command-o-f (open firmware command) and at the 0> prompt entering 
boot cd:,\install\yaboot 
but this fails with an error: can't OPEN: cd:,\install\yaboot

I have a feeling that the Ubuntu installers just don't like my CD drive.

I then tried to boot using the hard drive (hoping to then run the install CD) so I used OS 9 disk utility to format the internal hard drive as a Mac OS standard partition (HFS) and copied vmlinux, initrd.gz, yaboot and yaboot.conf files to the root level. Then with the alternate install 7.04 CD in the CD drive, started with the open firmware command and entered at the 0> prompt:
boot hd:9,yaboot    
(since 9 was the number of the relevant HD partition where yaboot etc was installed.)
I got the error message: Bootstrap partiton type is wrong: Apple_HF type should be "Apple_Bootstrap"

Hoping to be able to ignore that, at the boot: prompt I entered install (also tried: install video=ofonly) but that just got me:  Unknown or corrupt file system.

Not knowing how to format the drive as Apple_Bootstrap from a Mac system, I gave up.

Currently I have again formated the internal hard disk using OS X disk utility into 2 partitions of type Mac OS extended, and installed OS X on the second of the 2 partitions.

Can anybody give me some guidance on how to procede?  It would be greatly appreciated.

Thanks,

rjt1000

---

### Post by rjt1000 on 2007-09-17
OK, I made some progress on my own, although I am still having some problems.

I was able to follow pxwpxw's post [here]("http://ubuntuforums.org/showpost.php?p=2887410&postcount=4")
 which allowed me to boot from my HD and run the Feisty alternate install .iso from my hard drive.

Installation proceded well, but when it was time to boot into Ubuntu, I only got a command line interface. As far as I can tell, the installer did not install the gnome graphical interface

I tried to install the gnome interface with the command lines:

sudo aptitude install gnome-desktop-environment
and
sudo aptitude install xserver-xorg
and then configure with
sudo dpkg-reconfigure xserver-xorg
choosing to allow it to assess my hardware and use all the defaults

But I am still not able to boot into the graphical interface, and seem hopelessly stuck in the command line.

I would really appreciate it if anybody could help me troubleshoot this. I am well over my head in this as a Ubuntu newbie...

Many thanks to pxwpxw for the info that allowed me to get the alternate install .iso to install from the hard drive.

-rjt1000

---

### Post by pxwpxw on 2007-09-18
> **rjt1000 said:**
> OK, I made some progress on my own, although I am still having some problems.


The text console restart is normal if you installed the minimal command line (CLI) or server version (I'm not sure what is the default version).
Then  the simplest way is just install the ubunut-desktop package for gnome desktop (or xubuntu-desktop or kubuntu-desktop) if you dont need to be selective about the bloatware.

You may just need to install gdm to access the desktop, or some other packages to support it.
```

 find /etc -name *dm

```

You can see how big the installation is 
```

 df -h

```
command line install is less than 1 Gb, desktop can be 2Gb or more.

First of all, check if Xwindows is available - try
```

 startx

```

If you have Xwindows installed that should get either a graphical screen, or some error message, the full details are in /var/log/Xorg.0.log

Could also be a problem with the xserver-xorg default configuration for your system. If you need help there, try to to post a copy of /etc/xorg.conf and
/var/log/Xorg.0.log. 

You might need a xorg expert for that, or there are numerous threads.

---

### Post by rjt1000 on 2007-09-18
Thanks for you reply pxwpxw.

OK, I found out what was wrong. I thought I was checking the box on the installer to install the desktop environment, but on the 3rd try, I realized that I was just hitting enter at the highlighted option rather than first hitting the space bar to check the option first. This sure is humbling...

That did indeed install the gnome desktop!!

But unfortunately when I booted to the graphical interface, all I had was rolling lines. (wow how many things can go wrong:confused:  )

So back to the drawing board:

I found one post [here]("http://ubuntuforums.org/showthread.php?t=418301") from a Pismo user that suggested adding a modeline to the xorg.conf file. Not sure why, but that didnt work for me.

Googling found a [different potential cure]("http://lists.debian.org/debian-powerpc/2005/10/msg00409.html"): adding:

HorizSync     28-51
VertRefresh 43-60

to the xorg.conf.

That worked !!

So, finally, I have a useable Ubuntu desktop running on my Pismo, and this is my first post here, using Ubuntu.

Thanks again for your help, and for a forum like this to find the info to make things right.

-rjt1000

---

