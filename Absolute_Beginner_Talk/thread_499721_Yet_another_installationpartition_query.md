---
title: "Yet another installation/partition query"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-07-12
Hi all...(This is more me trying to understand partitioning than anything requiring urgent attention)

I have two hard disks - one 80Gb master and one 20 GB slave.

The 80GB master has four partitions. Feisty versions of Kubuntu, Ubuntu and Xubuntu on the first three partitions and a 1 GB swap. 

The Kubuntu installation is currently my root partition. I mount the Ubuntu and Xubuntu installations in /media/sda2 and /media/sda3

(For the record, I mainly use the Xubuntu partition as a storage partition and I rarely use the Ubuntu partition. But it's nice to have all three options in my grub)

I want to install an older version of Ubuntu (Edgy) on the 20GB slave drive.

My problem is that each time I install a new operating system the root partition changes, my grub changes, menu.lst changes and sometimes the UUID's change.

See attached screenshot.....I'm half way through installing Ubuntu Edgy on the slave drive and have reached the partitioner.

If I change partition 1 on my master drive (hda1) to root I'm assuming (from past experience) that the Ubuntu Edgy install will overwrite my Kubuntu Feisty install, which I don't want.

If I change partition 1 on my slave drive (hdd1) to root I assume grub will default to this partition at boot time and the three Fiesty installs will be "subservient" to Ubuntu Edgy, which I don't want.

All I want is Kubuntu Feisty to remain as root and Ubuntu Edgy to mount in /mount/sda4 

It's not an uncommon situation so I'm hoping it's a reasonably simple procedure.

All advice appreciated.

Regards
Miguel

---

### Post by overdrank on 2007-07-12
Hi I believe you are at the limit for partitions. You can have 4 partitions to the drive unless you have a extended partition and then you can have 3 partitions under that. :(

---

### Post by BobCFC on 2007-07-13
Side note... I would say you do not need three Feisties if you just want to switch between KDE,XFCE and Gnome.  You can install KDE, XFCE Fluxbox and Enlightenment as programs in normal Ubuntu and then pick one at the login screen by pressing the Change Session button.

This will save you many gigs and means you wont have 3 sets of scripts/drivers to set up etc.

You may have your own reasons such as testing.?


The root partition is relative to the OS you are currently in. So you will have four / which will see each other as ordinary drives.  You can change the **default** line at the top of /boot/grub/menu.lst to your preference (it starts at zero and include the recovery options).

You should be able to specify different root and place to install grub? I think the AlternateCD textmode installer lets you skip grub in expert mode?

---

### Post by Miguellint on 2007-07-17
Thanks for the replies and advice.

In the end I've ditched the 20GB drive and just installed an Edgy Ubuntu on the second partition of the 80GB drive (overwriting the Feisty Ubuntu installation).

This meant Edgy became my default O/S. But by editing the file /boot/grub/menu.lst on my first partition I managed to get Feisty Kubuntu back to the default O/S

Had to allow for the newly installed Edgy partition having a new UUID but, apart from that, no worries.

At least I gained a little more knowledge by doing another installation and having to edit the grub menu.

If anyone's interested, I decided to reinstall Edgy cos Feisty, K3B and DVD+R's don't get along on my machine. It sounds like the bug mentioned at...

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/91210](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/91210)

Bit of a nuisance but at least my workaround does the job.

Regards
Miguel

---

