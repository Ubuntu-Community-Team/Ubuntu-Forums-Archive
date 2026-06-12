---
title: "Installed Linux first then Windows now need to boot into Ubuntu"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by gmatt on 2006-07-12
Hello,

I installed Ubuntu a while ago and then I installed a windows partition on the same drive. Windows is the only option at boot time. 

I don't have a boot disk but I do have the Ubuntu install disk, is there a way I can mount the kernel image and boot it from the install prompt? I know there used to be a way with redhat.

---

### Post by Tom Brokaw on 2006-07-12
Pretty sure Windows writes over anything in the MBR or whatever.  I think you'll need to reinstall Ubuntu.

---

### Post by Jax Kovak on 2006-07-12
Don't reinstall Ubuntu, just get a hold of GAG ([http://gag.sourceforge.net/](http://gag.sourceforge.net/)).

Simply: Its a boot loader with very simple instructions that allows you to use it from a floppy or install it to your HD. I had a similar problem in not being able to boot Ubuntu and this saved my skin and allowed me to boot and re-install GRUB etc.

---

### Post by gmatt on 2006-07-12
All my musics on it....


:'(

---

### Post by gmatt on 2006-07-12
> **Jax Kovak said:**
> Don't reinstall Ubuntu, just get a hold of GAG ([http://gag.sourceforge.net/](http://gag.sourceforge.net/)).

Simply: Its a boot loader with very simple instructions that allows you to use it from a floppy or install it to your HD. I had a similar problem in not being able to boot Ubuntu and this saved my skin and allowed me to boot and re-install GRUB etc.

Dude, wicked Ima give this a shot. Love you guys. <3

World's a better place with you guys.

---

### Post by Tom Brokaw on 2006-07-12
Cool, I hope I'm wrong.  Good luck!

---

### Post by SigmaX on 2006-07-12
All you need is to get a new bootloader on the MBR.  Tom is right in as much as reinstalling Ubuntu would be the easiest way to go, because installing a new bootloader can get complicated (I used a Gentoo cd last time mine faltered :-P).

SigmaX

---

### Post by gmatt on 2006-07-12
Alright, GAG thing doesn't work, I get the error message "Boot sector not found or invalid", but it does see the linux partition(s).

I'm going to try a live CD. Music is too precious to give up.

---

### Post by gmatt on 2006-07-12
Question:

Does the alternative-cd help me in this situation? It says the following:

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 


I like the part about * installing GRUB to a location other than the Master Boot Record; Seems like it might be able to install Grub in the MBR...

---

### Post by Malac on 2006-07-12
I'm not sure but I think the Desktop Install CD has some sort of "repair/recover an installation" option.
Try that I think you can choose to just reload GRUB.

Hope this helps.

---

### Post by blip on 2006-07-12
I'm actually trying to do the same thing (though for different reasons) so I hope that this gets resolved.

---

### Post by gmatt on 2006-07-12
> **blip said:**
> I'm actually trying to do the same thing (though for different reasons) so I hope that this gets resolved.

I found the best way to fix it is to download the new distribution of Ubuntu which comes with a live cd, which instead of just a install option it gives you the option to run a Ubuntu desktop right off the CD. Through the desktop you can fix your problems. This is how I did it specifically.

1. Dowloaded new Dapper Drake Ubuntu Live CD/ Install CD (Ubuntu 6.06) found at [http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

2. Burnt the cd image and rebooted into it. Selected option 1. Install or Run Ubuntu from the list given by the live cd

3. When the desktop is finished loading I opened a terminal and started parted. I changed the the flag on the linux partition to boot and active (on).  The commands for me where something like:

>parted
>p (to get a list of partitions)
>set # boot on (where # is the number of your linux partition with grub on it)

If you have problems please ask. This is how I did it.

---

### Post by richbarna on 2006-07-12
How big are your Partitions/Harddrive.
Another idea is to use the ubuntu cd to partion and make a very small partition (3 gb). You can install another ubuntu on this partition, use the same swap file as your old ubuntu, and it will reinstall grub on the windows drive.

The good thing about this is, that grub will list 1 Xp and 2 Ubuntus, also you have 3 Gb to try other Linux distros :)

---

### Post by Jax Kovak on 2006-07-12
Glad you got things sorted. Shame about GAG!

---

