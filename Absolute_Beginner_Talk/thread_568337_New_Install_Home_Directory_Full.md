---
title: "New Install: Home Directory Full"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by dare dukes on 2007-10-05
Hi, all.  I just installed Feisty last night on a brand new Toshiba Satellite laptop.  I'm brand new to Linux.  (I have a mac at home for sound recording, among other things, but my job bought me a pc laptop, so i decided to dump vista and give ubuntu a try).  I'm a huge open source fan and thrilled to finally move to a Linux OS.

But...

When I installed I wiped away Vista--chose a 100% partition.  For some reason, the install didn't take (I don't remember what the issue was).  So I re-installed and chose a 75% partition.  That worked, but, when I tried to upgrade OpenOffice to 2.3, it said my disk was too full.  I ran the disk usage utility, and it seems like only 2GBs were allocated to my home directory, and it was all used up.  Then I tried to reboot, and I got a message saying I couldn't log on because the home dir. was full.

I'm thinking of just reinstalling now and seeing what happens.

I'd appreciate your help.  Thanks.

---

### Post by Pumalite on 2007-10-05
Use Gparted and make a partition of your whole drive, format ext3 if you want; then install>Guided>Use Entire Disk, or Manual, allocating at least 10 GB to '/', 500 MB to /swap and the rest to /home.

---

### Post by dare dukes on 2007-10-05
Thanks.  Any chance you could walk me through that?  How do I access and run Gparted?

---

### Post by Pumalite on 2007-10-05
Download this small iso, burn it to CD as image and then boot from it: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by benerivo on 2007-10-05
It is on the live cd that you installed from. It is in the main menu somewhere, so run this before you start the installation process. It is pretty straightforward. Just delete existing partitions, then make three new ones.

One will be 10Gb+ formatted as ext3
One will be 1GB+ formatted as  swap
One will be 'the rest of the drive' formatted as ext3

The install and choose manual partitioning select / for the 10GB ext3, swap for the 1GB swap formatted partition, and /home for the big ext3 partition.

---

### Post by Pumalite on 2007-10-05
The stand alone, burn to CD, boot from, program is newer more powerful, more flexible and gives you more control over the process.

---

### Post by dare dukes on 2007-10-05
I'm running from the Live CD.  I've deleted two partition, but there's a third extended partition "/dev/sda2" that is locked.  There are two sub-partitions (logical partitions?) that are also locked.  The information window reads "Busy (at least one logical partition is mounted).  So how do I delete these?

---

### Post by dare dukes on 2007-10-05
forget it.  just figured it out.

---

