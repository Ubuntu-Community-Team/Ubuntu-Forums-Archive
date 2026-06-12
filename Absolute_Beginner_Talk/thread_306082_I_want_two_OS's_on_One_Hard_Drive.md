---
title: "I want two OS's on One Hard Drive"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by tribeone on 2006-11-24
I would like to run mandriva as well as ubuntu on my pc. I have one HD can this be done?

---

### Post by taurus on 2006-11-24
Yes.  Just create three partitions, one for Ubuntu, one for Mandy, and one for swap.  Both Ubuntu and Mandy can share the same swap...

---

### Post by Kevin on 2006-11-24
Yes, you'll just need to partition the drive up using gparted from the live cd.  You'll need an ext2 partition for each OS, and you can use one swap partition for both.

Edit: I lose :p

---

### Post by mcduck on 2006-11-24
better use ext3 instead of ext2 ;)

---

### Post by tribeone on 2006-11-24
Can I partion the drive while I install mandy or do I do it before? I already have ubuntu installed.IS it the same process if I have windows xp? I wouldlike to do the samething to my laptop.

---

### Post by taurus on 2006-11-24
You can use the Ubuntu LiveCD to resize your partition first if you want...

---

### Post by tribeone on 2006-11-24
how do i do that? Sorry guy's I am a real nubbie at this.

---

### Post by confused57 on 2006-11-24
Here's some screenshots:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

homepage for gparted, the gparted live cd is only a 30 mb download:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Once you resize, you'll have unallocated space to install your new OS on, using the OS installation cd.

I use chainloading to boot multiple linux OS...you do this by selecting to install grub to the root partition of the OS you're installing...then add an entry to the grub that you use to boot your computer to boot your new linux OS, for e.g.:

title    Mandriva
rootnoverify   (hd0,3)
chainloader +1

(hd0,3) would be for root on the 4th partition.

You can install linux on logical partitions, so you can install several linux OS on one hard drive...there is a limit of 4 primary partitions on one hard drive, but one of the primary partitions can be "extended", within which you can have many logical partitions.
Here's 2 websites you might want to bookmark:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by nickburns on 2006-11-24
Another option is to put ubuntu as the main OS and user vmware to 'boot' up windows.  With this setup you can switch from windows to ubuntu without having to reboot the system.  I would only recommend it if you computer has a good CPU and memory.

Either way here is the installation instructions for vmware

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

---

### Post by tribeone on 2006-11-24
I was wondering after reading all this do I have enough space. I only have a 20 gb hdd.

---

### Post by 56phil on 2006-11-24
You should be OK, I once put Ubuntu on a 10GB drive.

---

### Post by nickburns on 2006-11-26
Well, that might be a bit too small for windows and linux, a clean install of ubuntu is less than a Gig (If I remember right), but windows xp SP2 is about 3 gigs.  The new vmware will allow you to grow the VM OS file as needed, although it does it 2 gigs at a time.  So you could go with ubuntu, install vmware, and set the VM OS to say 10 gigs, and as the VM OS grows it will slowly take up HD space.

---

### Post by tribeone on 2006-11-26
Thanks once again guy's. I got it installed and all is working well.

`

---

