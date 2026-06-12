---
title: "How do i dual boot"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-08-05
I want to install dual system.. both Windows XP and Ubuntu..

I have a 40 GB Harddisk

and i have partioned 
10Gb for root
1 GB for swap 
and the rest for my windows and my files

But when i go to the partitioner in Ubuntu Installer i just get the option to install on the 40Gb hdd and nothing more than that.

last time when i tried to do it it had gone fine but this time god knows what's the problem..

What should i do

---

### Post by steve.horsley on 2006-08-05
My guess is that it's not offering to use the free space because there isn't any. You can either use custom partitioning and tell it to use the 10G partition for root (tell it to reformat it) and the swap for swap, or somehow delete those 2 partitions and then the installer will be able to offer to use the free space. 

If you use custom partitioning, you are probably better off using the "alternative" installer rather than the rather flakey live-CD installer.

---

### Post by hardfire_avk on 2006-08-05
> **steve.horsley said:**
> My guess is that it's not offering to use the free space because there isn't any. You can either use custom partitioning and tell it to use the 10G partition for root (tell it to reformat it) and the swap for swap, or somehow delete those 2 partitions and then the installer will be able to offer to use the free space. 

If you use custom partitioning, you are probably better off using the "alternative" installer rather than the rather flakey live-CD installer.

Both the 10 Gb and 1 G patitions are totally empty. So i think that there would be no problem for space.
What is the alternative installer... I have a ubuntu breegy badger 5.10 CD with me..

---

### Post by kurniawands on 2006-08-05
> **hardfire_avk said:**
> Both the 10 Gb and 1 G patitions are totally empty. So i think that there would be no problem for space.
What is the alternative installer... I have a ubuntu breegy badger 5.10 CD with me..

no, no, what steve meant was the alternative cd. there are 2 version of installer, first is live cd and second is the alternative cd to download from ubuntu website. if you got some problem with the live cd, you might try the alternative cd.

live cd is the version that let you run ubuntu from the cd, with installer ready on the desktop, the alternative cd is (i think) installer only. my self, never try the alternative. the live cd is works fine with me, till now.

---

### Post by hardfire_avk on 2006-08-05
If that is what steve meant then i think i have been using the installer cd(alternate.. what u meant). cuz i have never installed from the live CD. Actually i even dont know how to install from a live CD

---

### Post by cstudent on 2006-08-05
Breezy Badger doesn't have the LiveCD & alternate CD options. You'll have to download a Dapper Drake iso in one of these options.

---

### Post by hardfire_avk on 2006-08-05
I have ubuntu 5.10 is that the breegy badger??..

However how do i install the dual system.. that's the main thing

---

### Post by Frank Golden on 2006-08-05
> **hardfire_avk said:**
> I want to install dual system.. both Windows XP and Ubuntu..

I have a 40 GB Harddisk

and i have partioned 
10Gb for root
1 GB for swap 
and the rest for my windows and my files

But when i go to the partitioner in Ubuntu Installer i just get the option to install on the 40Gb hdd and nothing more than that.

last time when i tried to do it it had gone fine but this time god knows what's the problem..

What should i do
The 11 GB for linux should be unallocated. Windows XP should be installed first on the beginning sectors of the HD. XP likes to be first.:rolleyes:  Linux can be anywhere physically on your drive. 
When you get to the LiveCD desktop doubleclick the installer. When you get to part about partitions choose the option to 
install to the largest free space. Ubuntu will create a ~10GB
ext3 partition for itself and a ~1GB swap from the unallocated space. The size of the swap will vary depending on the amount
of ram detected. Ubuntu will then automatically install itself
to those partitions. At some point GRUB will install, I believe
a dialog box will ask you if you want to do this choose yes.
When machine reboots you will see a boot menu. The default will
be Ubuntu first, which will boot automatically if you do nothing after 10 seconds. Ubuntu has last laugh about who's first.:razz: 
Use the arrow keys and enter to choose boot option.
Once booted into Ubuntu you can edit grub, using this command
[sudo gedit /boot/grub/menu.lst] without the brackets to change the boot order. Be careful editing menu.lst a mistake could
make your system unbootable. See link below for more info.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

As a matter of fact the site this is a part of is more
than you'll ever need for info on dual booting. It does use the
alternate CD but is very comprehensive. If you can't get the
LiveCD to work give it a read. As a matter of fact give it a read anyway, could keep you out of trouble. Remember if at first you don't succeed read the instructions. It has screenshots
too. Way cool.

---

### Post by steve.horsley on 2006-08-05
> **hardfire_avk said:**
> Both the 10 Gb and 1 G patitions are totally empty. So i think that there would be no problem for space.
What is the alternative installer... I have a ubuntu breegy badger 5.10 CD with me..

Wrong. If the space is allocated to partitions, then it is not free space, it is allocated. Free space is space that has NOT been allocated into partitions of any kind. Use whatever you used to create those partitions, and delete them. Then use the Ubuntu installer and it will offer to install into the free space (which it will use to create partitions for itself first).

---

