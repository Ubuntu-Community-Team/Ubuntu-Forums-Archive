---
title: "grub error no such partition"
date: 2011-11-22
forum: Apple Hardware Users
---

### Post by Dr. McKay on 2011-11-22
I have a dual boot setup on my imac with Snow Leopard and Ubuntu 11.10. I also installed the KDE plasma desktop environment from within Ubuntu.

However, I found to be a bit of a mess, having apps from both distros on my disk. Moreover, I can't really get used to Unity (bit of a Fisher Price interface, if you ask me). I've tried to install Classic gnome, it works, but I find that overall, Ubuntu's interface is jerky (including Unity) when compared to Kubuntu's beautiful and smooth plasma interface.

So I wanted to get rid of Ubuntu. I deleted my linux partitions (root and swap - for some reason, I had three swap partitions instead of the one I created at the start).
That left me with my OS X partition and 30Gb of free space. I then inserted my Kubuntu live CD, rEFIt detected it no problem, and installed Kubuntu (created partitions manually, 2Gb swap, and one 28Gb EXT4 partition).
Kubuntu installed without any error messages. Upon booting however, and choosing my linux partition in rEFIt, I got the message "Grub error... no such partition"

I've searched the web and found this :
[http://www.rajeshrana.net/2010/10/12/grub-error-no-such-partition-grub-rescue/](http://www.rajeshrana.net/2010/10/12/grub-error-no-such-partition-grub-rescue/)

Can this rescue my setup (it's for Ubuntu but I guess it'll work in kubuntu as well) ?

---

### Post by oldfred on 2011-11-22
I do not know Mac, but those are the standard commands for installing to the MBR of a PC not a Mac. You may have a hybrid gpt/mbr system (usually with Windows) and need to know the commands for a Mac. Does rEFIt use or read the MBR?

---

### Post by pindar on 2011-11-22
The problem may simply be that deleting and reformatting partitions made the partition tables on your hybrid MBR go out of sync. ReFit has a tool "sync partition tables" on its first screen; have you tried running that?

---

### Post by Dr. McKay on 2011-11-22
> **pindar said:**
> The problem may simply be that deleting and reformatting partitions made the partition tables on your hybrid MBR go out of sync. ReFit has a tool "sync partition tables" on its first screen; have you tried running that?

Yes, but that doesn't work. Always get the message "disk will not be touched".

Anyway, cleaned up everything, I'm back to one 320Gb OS X partition.
So, best way to install Kubuntu to dual boot with OS X ?

---

### Post by Dr. McKay on 2011-11-23
Anyone ?

I find the partition manager in Kubuntu less able than gparted. I couldn't erase my swap and root partitions from the live cd in kubuntu. Had to boot into ubuntu to erase the partitions. After that, I could resize my OS X partition with Disk utility without hiccups.

Also, the Kubuntu installer doesn't seem to be as good as the Ubuntu one, only giving the option of installing using the entire disk (thus wiping OS X as well) or manual.

So, installing Kubuntu.
I'm going to reinstall refit. Then, I suppose I'll have to manually create the linux swap and root partitions or can the kubuntu installer do that for me ?

---

### Post by Dr. McKay on 2011-11-24
Thought I'd try it on my own...

From my one OS X partition, I resized it again, reserving 35Gb for Linux. Used the Ubuntu live cd to create partitions with Gparted (the Kubuntu partition manager doesn't play ball for some reason), 1 2Gb swap partition,  rest as EXT4 root partition. 
Booted back into OS X, reinstalled rEFIt and then rebooted with the Kubuntu live CD. Installation went fine, but upon reboot, still got the grub error message.

Sighed, booted back up with the Ubuntu live cd, chose to erase and install ubuntu (thus keeping my OS X partition safe), rebooted without the CD : hey, presto ! 

Why couldn't I just do the same with the Kubuntu live CD ? In other words, why does the kubuntu installer suck ?
As far as I can tell, the only way to have Kubuntu on my imac, is to install Ubuntu and then to download Kubuntu-desktop from the software center.
It works, but having both Gnome and KDE apps in one place is a bit annoying. 
But I'm not complaining...

---

