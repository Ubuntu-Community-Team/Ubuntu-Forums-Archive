---
title: "Gparted"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-24
Am I missing something or is gparted not able to edit ext3 partitions?

I want to shrink the size of the partition that ubuntu is installed on and increase the size of my fat32 storage drive.  But gparted won't let me move or resize my ext3 partition.

---

### Post by tuxinvader on 2006-03-24
You can't resize a mounted partition, your best bet would be to boot from a LIVE cd, but I'm not sure if that would include gparted?

I resized a partition using the install cd yesterday using the rescue boot option, but that was just an extended partition. I had to mount the root partition and copy parted and a few libs onto the ram disk, then unmount the root partition and run parted.

When you get to the shell:

cp /target/sbin/parted /sbin
cp /target/lib/libparted* /lib
cp /target/lib/libncurses.5* /lib

There were a few others, but if you try and run it it will tell you what libs it can't find. Copy them all over until it runs and then unmount /target and make your changes.

---

### Post by drl on 2006-03-24
Hi.

The SF GParted page points to a LiveCD, but I have not tried it ... cheers, drl

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by gigi1234 on 2006-03-24
I have tried the Gparted live cd and it works like a charm. Just download the iso file and burn it, then reboot with the live cd. Good Luck.

---

### Post by akiro.yamamoto on 2006-03-24
I have not had a chance ( or reason ;) ) to try this yet but it's looks like it might ne worth a shot: [**CLICK ME! **](http://www.sysresccd.org/Main_Page)

---

### Post by drl on 2006-03-24
Hi.

OK, I downloaded the LiveCD I mentioned at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and burned it.

It booted and I was able to see the partitions on my disks.  I have SATA and IDE drives on this box.

I did note that qparted was [COLOR="Red"]not[/COLOR] able to do anything with LVM partitions -- not even recognize them.  The LVM package and scheme is an installation option in Ubuntu, RedHat, and SuSE.  The LVM package might include some utilities to the same work as qparted, but I have not yet investigated that.

Otherwise, follow the advice in this thread, and I think you will be successful.  When we say *successful,* we mean that we trust you have backed up data of value before you start doing anything significant, especially with partitions.

Best wishes ... cheers, drl

---

### Post by WoodyMahan on 2006-03-24
OK.
GPartEd Live CD worked.  I resized the ext3.  I then copied my small Fat32 into the newly opened space.  That didn't work as well as I wanted so I logged into Windows and reformatted the large drive to NTFS.  THEN I went back into Ubuntu and reformatted that partition to Fat32.  Now I have 15 GB for Windows, 8 GB for Ubuntu, 13 GB Fat32 Storage1, 36 GB Fat Storage2, 3GB Swap.  Not perfect, but I don't feel like messing around with it anymore and I have all of my sotrage space available now.  Rock On Ubuntu.

---

