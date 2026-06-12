---
title: "dualboot linux/xp"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by slobber on 2008-02-17
have installed ubuntu7.10 onto 40Gb slave harddrive now trying to configure system to boot to either OS at startup .HOW???:confused:

---

### Post by nonewmsgs on 2008-02-17
did you install windows first?  how many drives do you have and are they all pata or all sata or a mix?

---

### Post by slobber on 2008-02-17
Have Got Win Xp On 160gb Sata Master With 4 Partitions I Use My Computer For Business And Personal Use And Have A Wired Home Network To My Office Computer For Backup. Using 40gb IDE Slave To Learn About Linux And Am Tying To Find A Simpler Way Of Switching Between Harddrives Than The Full Reboot Via Start Menu To Boot Into Linux

---

### Post by jcitguy78 on 2008-02-17
do you get the gurb menu at startup?

---

### Post by kyphi on 2008-02-17
Running 2 operating systems means rebooting in order to switch from one to the other......unless...

You use a virtualisation programme such as VirtualBox, in which case you run one operating system within the other.

The choice you need to make is which operating system is going to be your primary system.

I run XP in Ubuntu for the limited time I find it necessary to use XP.

Mixing PATA and SATA drives is not a good idea - I would recommend to ditch the PATA drive and replace with SATA.

Good Luck.

---

### Post by Efros on 2008-02-17
I have Ubuntu installed on a master IDE drive with XP on the slave, I can select the boot partition from the grub menu, or if I choose my motherboard's BIOS will reassign master and slave boot order which will boot the slave disk. I have also installed XP within Virtualbox, what I have found is that I only use XP for a couple of recalcitrant (read non WIne compatible) programs that I can't do without. Consequently I haven't been inside my non-virtual windows environs for weeks. Ubuntu has integrated well with our network at work and I can access shared network drives from within the virtualbox and indeed within Wine. On a X2 3800 with 1Gb of memory the Virtualbox XP is up and running much faster than XP on HD.

---

### Post by slobber on 2008-02-18
> **Efros said:**
> I have Ubuntu installed on a master IDE drive with XP on the slave, I can select the boot partition from the grub menu, or if I choose my motherboard's BIOS will reassign master and slave boot order which will boot the slave disk. I have also installed XP within Virtualbox, what I have found is that I only use XP for a couple of recalcitrant (read non WIne compatible) programs that I can't do without. Consequently I haven't been inside my non-virtual windows environs for weeks. Ubuntu has integrated well with our network at work and I can access shared network drives from within the virtualbox and indeed within Wine. On a X2 3800 with 1Gb of memory the Virtualbox XP is up and running much faster than XP on HD.

strange coinsidence I'm running exact same CPU and memory as yourself but still have a long way on learning curve before i can even think of using Ubuntu as my main OS . All company records still within windowXP .never mind by boot problems how do I access all my info from Ubuntu do i have to copy everything to dvd and then to Ubuntu.What is the grub menu? and how do you set up virtual box .

---

### Post by kyphi on 2008-02-18
> how do I access all my info from Ubuntu

You create a mount point for your Windows partition and then you can read the files from Ubuntu.  To do that see  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

> What is the grub menu?

GRUB stands for Grand Unified Bootloader and enables you to select any installed operating system.  Windows uses a MBR (Master Boot Record) which has a similar function.  The GRUB menu is installed when you install Ubuntu.

> ...how do you set up virtual box

You install VirtualBox and follow the instructions in the VBox manual.  Once installed you will need to install Windows in the VirtualBox installation (a fresh install).  This does not affect your present Windows installation.

---

### Post by adza on 2008-02-18
I have 4 HDD (2 * IDE and 2 * SATA) installed in my machine at home, with the windows install on the SATA and the linux install looking at the IDE drives. To get the system to boot into grub was relatively simple, i just entered the BIOS in my machine and set the boot priority of the drives to the IDE with the linux install on it. This way it calls the GRUB rather than the windows MBR and the GRUB recognises that there is a windows install on the other drives and displays the option of where to boot into... the windows MBR doesn't play that nicely :)

---

