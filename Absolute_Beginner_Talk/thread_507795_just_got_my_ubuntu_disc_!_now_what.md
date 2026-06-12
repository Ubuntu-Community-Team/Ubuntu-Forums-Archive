---
title: "just got my ubuntu disc ! now what ?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by linv5800 on 2007-07-23
hi all , new to this system but want to try it out .. im running a vista - xp dual boot right now with a partition
for ubuntu ... can this be done and how ? im using vista boot pro to dual boot . 
thanks all and im very happy to be here ! much appreciated .:popcorn:

---

### Post by the.dark.lord on 2007-07-23
Just pop in the disc, and reboot.

Follow the instructions, and enjoy :) .

---

### Post by Irony on 2007-07-23
Boot up in windows put the disc in and reboot to see the live CD - this doesn't install anything and won't affect your current install - its just running ubuntu off the cd.

Make sure sure you have the CD as first boot set in the bios or else nothing will happen and you will boot up in windows as normal.

Assuming you like the live CD hit the install icon and install to the freespace, choose the default options to install to the freespace - assuming the free space is at the end of the drive ubuntu will divide this free space into root and swap.

If it asks about home just accept the default of installing in to root partition.

Note accept the default of installing the grub bootloader to the MBR and this will detect your windows install.

---

### Post by Majorix on 2007-07-23
When asked choose "use the largest continuous free space" under partitioning. Otherwise Ubuntu might use the whole disk so be careful.

---

### Post by linv5800 on 2007-07-23
Thanks , ill give it a try .. do i need to boot from dvd ?

edit - answered my questions before i re-posted ! appreciated

---

### Post by ZacDavis on 2007-07-23
Make sure you back-up all of your "sensitive files" and anything you want to keep.  Otherwise, you might be in some deep doo-doo.

---

### Post by Dr Small on 2007-07-23
It depends if your disc is dvd or cd.

---

### Post by LaRoza on 2007-07-23
> **linv5800 said:**
> Thanks , ill give it a try .. do i need to boot from dvd ?

Yes. Put it in the disk tray, turn off computer and turn it back on. (or restart).

---

### Post by rahul_bhise on 2007-07-23
now the real game start
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by linv5800 on 2007-07-23
when i go to install on a partition , ubuntu says there is no root to install and to make a another partition on that drive , if i do that , will it erase the entire drive ?
i have tons of stuff i dont want to lose..

---

### Post by linv5800 on 2007-07-23
also , besides needing help in the above post , is most software compatable with this?

---

### Post by kinematic on 2007-07-23
what is it you need help with and what software are you talking about?
you need to be more clear,we're not mindreaders.

---

### Post by linv5800 on 2007-07-23
> **linv5800 said:**
> when i go to install on a partition , ubuntu says there is no root to install and to make a another partition on that drive , if i do that , will it erase the entire drive ?
i have tons of stuff i dont want to lose..

can you not read ? 
how much more clear do i need to be ? 
theres no need to be s@itty to someone new when YOU  are the one offering help .:)
don't need your help anyway , ill either figure it out , i always do , or
someone who's really here to help will help me .

---

### Post by deadlikeoscar on 2007-07-23
Is your whole hard drive partitioned with one XP and one Vista partition? If so, you need to make room for Ubuntu. I couldn't quite tell if that was what you meant in your first post. Even if you have free space on the drive, Ubuntu can't find a partition for itself and won't install. You will have to resize one of your partitions or buy a second hard drive if you want to play it safe. If you already have an Ubuntu partition set up, is it partitioned as NTFS or Fat32 or something. If you are positive that made a partition for it--it must be a Linux compatible file system, such as ext3. Don't get offended if you have already answered these questions, I just want to make sure that I FULLY understand your situation before I go off saying, "Yeah, go for it." and then you erase your drive, y'know? It would be awesome if I could see a screenshot of your partitions but that might be kind of difficult in this situation.

A lot of Windows software can be run through a program called Wine if there is no Linux port available. Although a lot of Linux specific software is as good or better than many Windows versions. I think that Amarok is way better than say, iTunes and K3B is as capable as Nero. Those are both KDE apps but they install and run fine in Gnome (Ubuntu's default) as well. If you use torrents much, Deluge is a great uTorrent replacement or you can run uTorrent in Wine if you prefer. This is a long way of saying that you should be fine with software on Linux.:)

---

### Post by rillip on 2007-07-23
Some programs work in Wine. Don't count on it, though.  If you MUST run Windows designed software, leave Windows installed somewhere.

As for the partitioning, I recommend you review the links about partitioning and install here:

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Essentially, defrag, resize a partition, use the free space to make at least two new ones (swap and root), and install to those partitions.  SHOULD not affect your files, but COULD cause partition corruption on the resized partition.  This is very rare, but make sure you make a backup just in case.

---

