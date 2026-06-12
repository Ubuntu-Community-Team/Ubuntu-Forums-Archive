---
title: "Formatting drive for ONE installation of Kubuntu"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Piney Woods on 2005-12-18
I have a rather unusual problem.  I'm trying out different distros of linux and have come to like Kubuntu.  I've heard enough about SuSe that I wanted to try it too.  Then came Fedora Core.....needless to say I started salivating for it as well.  Soooo....I thought, why not a mulitboot linux system?  I read where it was easy enough so I took the plunge.  Now...I have around half a dozen installations of Ubuntu on one hard drive and I want to change that.  However, I have used my trusty windows 98 boot disk to partition and format the drive.  Funny thing is......linux is STILL THERE!..........I have no idea why.  I have even told it through the ubuntu installer to ERASE the ENTIRE drive and repartition the drive....well....afterwards, near the end of the install it says it STILL finds ubuntu on the drive!  How????  What am I missing?  How do I get rid of it and go back to just Kubuntu?  Will I have to do a low level format perhaps?

Maybe I just don't understand the linux file/partitioning system yet.  I'm used to zapping a drive with my 98 boot disk.......HELP!

Piney Woods

---

### Post by kairu0 on 2005-12-18
It sounds like it might be an MBR problem.

Boot from that trusty, old floppy (usually the latter :) ) and double-check that you have no partitions. Then, exit fdisk and run a "fdisk /mbr" to clear the Master Boot Record. That should remove the lingering Ubuntu boot loader that the installation program detects to be an Ubuntu installation.

---

### Post by Piney Woods on 2005-12-18
[QUOTE=kairu0]It sounds like it might be an MBR problem.

Boot from that trusty, old floppy (usually the latter :) ) and double-check that you have no partitions. Then, exit fdisk and run a "fdisk /mbr" to clear the Master Boot Record. That should remove the lingering Ubuntu boot loader that the installation program detects to be an Ubuntu installation.[/QUOTE]


So it's not so much that there are multiple installations just multiple mentions of it in the mbr?  :confused:

---

### Post by kairu0 on 2005-12-18
[QUOTE=Piney Woods]So it's not so much that there are multiple installations just multiple mentions of it in the mbr?  :confused:[/QUOTE]

That's my best guess.

Okay, so, you choose your partition option, it goes through without a hitch, and then you get stopped at the end of the installation right? At the end of the installation, (k)ubuntu tries to add the bootloader (called Grub) to the MBR.

When you delete partitions, the MBR does not get erased. So, you'll need to erase it yourself (fdisk /mbr).

If you are not familiar with MBR, here's a definition:

[http://isp.webopedia.com/TERM/M/MBR.html](http://isp.webopedia.com/TERM/M/MBR.html)

---

### Post by Piney Woods on 2005-12-18
[QUOTE=kairu0]That's my best guess.

Okay, so, you choose your partition option, it goes through without a hitch, and then you get stopped at the end of the installation right? At the end of the installation, (k)ubuntu tries to add the bootloader (called Grub) to the MBR.

When you delete partitions, the MBR does not get erased. So, you'll need to erase it yourself (fdisk /mbr).

If you are not familiar with MBR, here's a definition:

[http://isp.webopedia.com/TERM/M/MBR.html](http://isp.webopedia.com/TERM/M/MBR.html)[/QUOTE]

Yes, I'm familiar with the mbr.  I tried that and still get the same cluttered option menu for multiple kubuntu's.  I went to A: and did fdisk/mbr and then c:fdisk/mbr        I then reinstalled Kubuntu...checked the bootup and ..you guessed it....LOL...ANOTHER mention of Kubuntu.

Another other suggestions???

---

### Post by lorenco on 2005-12-18
if you get a clutterred startup screen from grub, it comes from /boot/grub/menu.lst

It is possible to edit this file (as root) and check where this comes from.

Normaly Grub will use like  hd(x,y) {where x & Y are numbers and represents x, the disc and y, the partition}

Disc one = 0, two = 1 etc...
Partition one = 0, two = 1 etc...
The first HD First partition will be "(hd0,0)... "

Find all the entries for the old linux installs and it shoud give you an idea where they are located

Also try "parted /dev/hda" or b or c... this is a good (and unix user friendly) partition tool in Ubunutu (and other good distro's):razz:

---

### Post by kairu0 on 2005-12-19
[QUOTE=Piney Woods]Yes, I'm familiar with the mbr.  I tried that and still get the same cluttered option menu for multiple kubuntu's.  I went to A: and did fdisk/mbr and then c:fdisk/mbr        I then reinstalled Kubuntu...checked the bootup and ..you guessed it....LOL...ANOTHER mention of Kubuntu.

Another other suggestions???[/QUOTE]

When you say multiple, how many are you talking about?

I only have one Ubuntu installation installed and I have 3 different Ubuntu options on my boot up screen (Ubuntu, Ubuntu failsafe, Ubuntu memtest, test.) You are not counting those are you?

---

### Post by lorenco on 2005-12-19
Good point.  That was my next quetion ... :D

---

