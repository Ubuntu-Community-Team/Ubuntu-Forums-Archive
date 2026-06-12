---
title: "Installing windows xp after ubuntu?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-03-20
I am looking for instructions on how to install windows xp in a situation where Ubuntu is already installed as the sole OS.

(I need Photoshop and haven't been able to get it to work under Wine)

---

### Post by dRock1286 on 2007-03-20
I'm not sure about installing winxp, but have you tried to use GIMP in place of PS?  I used to use PS all the time but find GIMP to be pretty close (but not entirely) to offering all that PS has to offer...

---

### Post by Efwis on 2007-03-20
you could always set up vmserver, load windows in it adn then put the program(s) you need on there. 

As far as I know, there is now way to install windows after Linux, because windows rewrites the MBR. MS wants their operating system to be primary on all computers because they feel they are far superior to anything else out there.

---

### Post by PartisanEntity on 2007-03-20
Been trying to use Gimp but compared to PS it is by far inferior to the point it is annoying. Have you compared the text editing features in Gimp and PS? That alone is driving me up the wall.

---

### Post by PartisanEntity on 2007-03-20
> **Efwis said:**
> you could always set up vmserver, load windows in it adn then put the program(s) you need on there.

Been there, done that. Many features are greyed out in PS under vmware.

---

### Post by sad_iq on 2007-03-20
You could try Photoshop 7 under CrossOver Office ([http://www.codeweavers.com/products/cxoffice/)](http://www.codeweavers.com/products/cxoffice/)), it works!!!
I'll try to find an answer to your question also...just takes a minute!!!

---

### Post by orb9220 on 2007-03-20
Basically xp overwrites the MBR because it thinks it is the only OS. So after xp is installed there will 
be no grub. Just restore grub by method in link.

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by Efwis on 2007-03-20
> **orb9220 said:**
> Basically xp overwrites the MBR because it thinks it is the only OS. So after xp is installed there will 
be no grub. Just restore grub by method in link.

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

The problem with that is that the OP might be only using one HDD, therefore installing windows will remove Ubuntu since it will repartition the HDD without thinking about any other OS on it.

---

### Post by PartisanEntity on 2007-03-20
> **Efwis said:**
> The problem with that is that the OP might be only using one HDD, therefore installing windows will remove Ubuntu since it will repartition the HDD without thinking about any other OS on it.

I think I can overcome this by making a partition for windows using gparted live-cd.

---

### Post by sad_iq on 2007-03-20
Found this link...it's got pictures and the lot...don't know if it works though.. just take a look :popcorn: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by hrp2171 on 2007-03-20
The GIMP might be just fine running in a virtual or emulated environment.  However, I would not run PhotoShop in such environments.  As mentioned in an earlier reply, some options were grayed out probably due to insuficient resources.  The speed of the virtual/emulated environments is going to be much slower than the real thing.  For example, the available RAM is going to be just a fraction of what could be available in a real time environment.

Yeah, I know these issues might change once virtualization becomes part of the hardware, but for the time being, I would only use virtual machines or emulators for trying out other OSes and not for running mission critical applications.  This is my opinion as far as home/hobby computing goes.

---

### Post by highfructose327 on 2007-03-20
I loaded XP after Ubuntu, I used GParted LiveCD to partition the HD I made a Ubuntu(ext3) partisan, swap partition and XP(NTFS). GParted was great here is a link [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
XP load to NTFS partition no problem. Only glitch was I did have to reload GRUB. I used the link mentioned above[http://http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub]("http://http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub")and follwed the user Remmelt's instructions. Best of Luck!!

---

### Post by PartisanEntity on 2007-03-20
Right, I have gone and messed up my perfectly working Edgy, HELP! :)

I followed this [how to]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

After booting from the live cd and going to the terminal to do:

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)

I then rebooted and the grub loader appeared, I chose my Edgy installation but then received an Error 17 with a message about not being able to mount the patition.

If I launch Genome Partition Editor or the gparted live cd my entire hard disk shows up as unallocated.

I would really appreciate some help :)

---

### Post by RealG187 on 2007-03-21
This is kinda related, but can I install ubuntu after XP?


I think I might need to reformat, cuz I cant change my partitions after I make them can I, I have no room to add another one, and I can't  make my ohter ones smaller can I?

---

