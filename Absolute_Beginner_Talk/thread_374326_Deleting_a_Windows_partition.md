---
title: "Deleting a Windows partition"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by chio on 2007-03-02
When I first installed Ubuntu, I set it up to dual-boot with Windows XP. I've since discovered Virtualbox, which lets me run the few Windows programmes I actually need to run without having to reboot. So how do I now go ahead and remove the Windows partition and free up the 20GB of space? 

Opening gparted brings up a visualisation of my partitions, but options to remove or resize them are greyed-out. Can anyone help?

---

### Post by Patrick K on 2007-03-02
You have to unmount it first. You can do that in GParted or several other places including Nautilus, and fstab.

---

### Post by kinematic on 2007-03-02
if those options are greyed out your windows partition is probably mounted or not in fstab?(i have no experience whatsoever with ntfs)
easiest thing to do is to boot from your ubuntu disk and format the partition as ext3(or whatever you desire).
after that you can mount it in ubuntu with:
> sudo mkdir /media/whateveryouwanttocallit
> sudo gedit /etc/fstab
and put this line in fstab
> /dev/hda#    /media/nameyouwant    ext3    defaults   0  2
and> sudo mount -ato mount it. 
you don't have to use /media to mount it...you can make a directory and call it what you want.

---

