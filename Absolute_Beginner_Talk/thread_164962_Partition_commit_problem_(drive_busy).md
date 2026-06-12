---
title: "Partition commit problem (drive busy)"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-04-23
I installed Ubuntu onto a 100 GiB laptop drive with two partitions. One for Ubuntu, and one swap. I left 26 GiB of space free of all paritioning thinking I would later come in and dual-boot XP.  However, I am so in love with Ubuntu now that I have it up and running, I decided I'd rather take that 26 GiB and use it in Ubuntu.

Problem is: I go into Disks Manager and partition it format it as ext3, mount it to a directory, and enable it and everything works great.  I can navigate to it and copy things to it.   However, when I reboot it's gone and upon looking at Disks Mananger again, it's unmounted and and disabled.

Which feels like I'm lacking a "commit" to the partition and mount.

I got my hands on QTparted and Gparted.  Both allow me to do roughly the same thing.  But when I got to commit the changes it says Drive Busy and gives an error.  QTparted advises me to unmount the drive before commiting the changes.  And how am I to do that when I'm running Ubuntu from the same drive?

Does anyone have any advice on this?  I'm sick of seeing a big red FAILED under Local File Systems when I boot Ubuntu and I'd like to gain regular use of those 26 GiB.

Thanks,

Craig Mitchell, St. Louis, MO

---

### Post by Sef on 2006-04-23
> I got my hands on QTparted and Gparted. Both allow me to do roughly the same thing. But when I got to commit the changes it says Drive Busy and gives an error. QTparted advises me to unmount the drive before commiting the changes. And how am I to do that when I'm running Ubuntu from the same drive?

If the drive is mounted you can't use that drive to unmount.   What you need is a separate disk: either a Live CD, or a cd of gparted or qtparted.  

[http://www.ubuntu.com/download]("http://www.ubuntu.com/download")

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

[http://http://qtparted.sourceforge.net/]("http://http://qtparted.sourceforge.net/")

---

### Post by garner_nc on 2006-04-23
You need to add that partition to your /etc/fstab file. You need to add a line to mount this partiton at boot. If you don't, as you've seen, you'll lose your mount at re-boot.

All the Best,
Doug White

---

### Post by mybootorg on 2006-04-23
Thanks, Doug!  After working with and tweaking Ubuntu this weekend, that's that was the last bugaboo problem I needed to fix.  Indeed, editing /etc/fstab to mount the drive worked.   I have to wonder why Drives Manager didnt offer an option to commit to fstab.  But oh well, I guess no matter how simple Linux becomes, you still have to edit some text files, eh? :p

---

### Post by garner_nc on 2006-04-23
Glad I could help. It's been a long Linux road for me, worth every minute!

All the Best,
Doug White

---

