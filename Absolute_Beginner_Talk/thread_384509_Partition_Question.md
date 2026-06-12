---
title: "Partition Question"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-03-14
After looking around the forums and various other sites, I still haven't decided the best way to install lUbuntu. I have a notebook computer, with a 100GB hard drive of which 75GB is taken up, I also have a 250GB external hard drive of which 100GB is taken up. So the question is, should I partition the external hard drive and install linux on there, or should I partition the main har drive and install it on there, or is there a better way?

Thankyou for your time 

ajeffreys

---

### Post by deathbyswiftwind on 2007-03-14
Anyway you could move some files off the internal to the external to free up some room? Its always best to keep it internal because linux doesnt like all external devices.

---

### Post by ajeffreys on 2007-03-14
However, would partitioning the internal har drive have a chance of deleting my XP install, as I don't think i will be able to get it back?

---

### Post by AtrejuT on 2007-03-14
what is using up so much space on your internal HD? What I'd suggest (though I don't know what kind of data you are dealing with) is moving most of it to the external HD (e.g. movies, music, pictures, that kind of stuff) then partitioning the internal HD to hold partitions for both, ubuntu and linux.
Just to give you an idea, I also have a notebook with 100GB internal HD and I use them as follows:
- roughly 20 GB for windows
- roughly 20 GB for linux /
- roughly 50 GB for linux /home
- a couple of GB for swap (though I rarely need that)

If you decide to do something similar you can mount your external HD inside your homefolder having it accesible right there.

Either way, it's probably easier to install Ubuntu to the internal HD.
The other option (IMHO not as good as the first) is making a partition for ubuntu / on your internal HD but mounting the external HD directly to /home

atreju

---

### Post by ajeffreys on 2007-03-14
Thankyou very much for the help so far. All my music takes up that space :). So if my external hardrive uses the FAT32 file system, would i be able to access all my music on the external hard drive with both Ubuntu, and XP.

---

### Post by dstew on 2007-03-14
Ubuntu and XP both can read and write FAT32.

---

### Post by Neobuntu on 2007-03-14
Put all your "stuff" (That you can't live without), on the external.

Run Windows checks and make sure your NTFS XP partition is error free or you may be barred from resizing, with a partitioner.

Don't just copy your Kubuntu CD iso file to a CD, you must "burn" it as an "image" to a blank CD (or wait weeks for it to come in the mail).

Boot a "K"ubuntu "Dapper" Live CD (Trust me, you can upgrade later. Use self-control).  Use the "Alternate" Kubuntu Dapper CD for 128 to about 256MB RAM. This is Xubuntu territory but I personally prefer Kubuntu tweaked better. It's all good (and *ubuntu). :P

Run Qtparted on the Kubuntu Live CD. (Some people have better luck with the Gparted-only LIVE booting CD. It's small.) 

Resize your internal drive in half. (No partitions, no formating.)

(Don't freak out later when Windows rechecks the drive for a smaller size, on an XP boot.)

Run the Installer on the Kubuntu Dapper Live CD's "Desktop". Point it to the blank space. One does NOT have to delete Windows and you won't, unless you tell it to use the entire drive (duh).

Let it do ALL the rest. It will make the partitions (/ and swap) in the new blank space after your Windows partition; for you. it will decide the swap size. it will format them (ext3 and swap) and do everything else in about 20 minutes on a newish computer. (Pick your short user name carefully, everything else is easily changed.)

You will wind up with a (GRUB) dual boot menu with a (*)ubuntu kernel and Windows to choose from (Which you can fancy up later by editing "/boot/grub/menu.lst", as root/administrator/superuser.

Problem solved.

P.S. It's no big deal if you prefer Gnome and wish to install Ubuntu instead of Kubuntu. KDE is more like the Windows UI (the good parts) and more suited to most new users taste, upon a fresh install.   

#1 You can run Gnome or KDE based programs in either; without restriction. 

#2 You can install both the kubuntu-desktop packages and the ubuntu -desktop packages and login to either; at any time. Yet, there will be a small penalty when upgrading more, rather than less packages.

---

### Post by Neobuntu on 2007-03-15
I hope that helps someone. :KS

---

### Post by dstew on 2007-03-15
Well said Neo.

---

