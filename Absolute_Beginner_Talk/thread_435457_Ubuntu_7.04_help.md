---
title: "Ubuntu 7.04 help"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by supersi on 2007-05-06
I want to run Ubuntu 7.04 (I believe it's 64 bit capable). I downloaded and burnt a bootable cd-rom.
The hardware I have is an AMD dual core 4200 processor/sata mobo/ 1 x seagate 320GB SATA drive (Vista 64 on C:)/ 1 x seagate 80GB IDE Drive.

I want to install Ubuntu onto the 80GB IDE drive and dual boot with Vista.

Step 1. How to install Ubuntu onto IDE Drive.

Can both HD's be connected when installing?
Should the IDE have a jumper on for Master?
Set hd boot priority to IDE drive?
Should I pre-format drive (I use Partition Magic 8.0), how should I format?
After formatting the HD I put the CDROM as boot device 1.


Step 2. 
Sometimes I have managed to install Ubuntu but I can't exactly remember the steps I took.
It just hangs on the pretty Ubuntu logo and progress bar.

Is this a corrupt install, so do I need to download again?
If not how do I fix it?

This is as far as I have gotten. I'd love to ditch Microsoft products and use Linux but i can't seem to get it to work.

---

### Post by igknighted on 2007-05-06
> **supersi said:**
> I want to run Ubuntu 7.04 (I believe it's 64 bit capable). I downloaded and burnt a bootable cd-rom.
The hardware I have is an AMD dual core 4200 processor/sata mobo/ 1 x seagate 320GB SATA drive (Vista 64 on C:)/ 1 x seagate 80GB IDE Drive.

I want to install Ubuntu onto the 80GB IDE drive and dual boot with Vista.

Step 1. How to install Ubuntu onto IDE Drive.

Can both HD's be connected when installing?
Should the IDE have a jumper on for Master?
Set hd boot priority to IDE drive?
Should I pre-format drive (I use Partition Magic 8.0), how should I format?
After formatting the HD I put the CDROM as boot device 1.

Both hard drives can be connected, be careful to only install to the one you want to overwrite

Master/Slave jumpers have no bearing at all.

Setting HD boot priority to the linux drive is a good idea because it will keep the linux bootloader on that drive.  It can boot other OS's like windows, so always booting from there is a good idea.

Format AND partition with the Ubuntu partitioner (gparted).  DO NOT use partition magic with linux, there can be issues sometimes.  If you want to give the whole drive to Ubuntu just select "use entire drive" during the install and it will format and partition as needed.  You can also choose to resize a partition if you prefer.

Yes, boot the CD drive first and run the LiveCD.  When you are ready to install, use the installer on the live CD and follow the instructions.  Should be straight forward.

---

### Post by scrooge_74 on 2007-05-06
You can check this website [http://www.psychocats.net/](http://www.psychocats.net/)

and also the documentation [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by cptjaben on 2007-05-06
Your going to want to run the Live cd and use a program called Gnome Partition Editor(System>administration>Gnome Partition Editor) to resize your 80gb harddrive. Then install ubuntu on the new partition and you should be set. You can resize the drive with another program such as Partition magic, if so your going to need a primary partition for the ubuntu install itself, your going to want this to be formatted ext3. Also you will need a 2-3gb swap partition. as far as your other concerns go, i wouldn't change anything. However if you have problems installing, you may want to look into those issues. Goodluck.

---

### Post by alienexplorers on 2007-05-06
When you make the partitions on the drive you are installing Ubuntu on I would setup 3 partitions.

Make one partition ROOT (/)
Make one partition HOME (/home)
and make the smallest (3GB) SWAP

By making a /home partition your preferences are saved there in case you ever have to re-install Ubuntu.

---

### Post by igknighted on 2007-05-06
> **alienexplorers said:**
> When you make the partitions on the drive you are installing Ubuntu on I would setup 3 partitions.

Make one partition ROOT (/)
Make one partition HOME (/home)
and make the smallest (3GB) SWAP

By making a /home partition your preferences are saved there in case you ever have to re-install Ubuntu.

3 GB of swap is a waste.  Really, anything over 1GB is, unless you have a laptop with more than that amount of RAM and want to use the suspend function.

---

