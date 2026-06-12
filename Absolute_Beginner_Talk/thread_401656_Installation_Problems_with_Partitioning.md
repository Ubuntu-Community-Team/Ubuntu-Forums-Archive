---
title: "Installation Problems with Partitioning"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Kanybus on 2007-04-04
Ok so after 6 months of playing with Ubuntu on my laptop, I decided I want to install it on my desktop.  I've found that want and do are two completely different ideas with me some times :)  Here's my problem:

The installation runs smoothly untill it comes time to make a partition.  I've tried manually setting the partition size and allowed Ubuntu to install on the largest continuous space.  That's where it hangs.  I even let it work over night and in the morning instead of hitting next I had to hit cancel set up.  

Does ubuntu have a problem installing on SATA drives?  More so I should say linux because SLED couldn't partition itself onto my hard drive either.  I can't format my whole drive untill I back up everything, and even then I will still need to install windows either directly or on a VM because my wife needs it for school and work untill OOo can figure out how to seemlessly work with MSo docs.  Please any assistance would be great!

---

### Post by mikewhatever on 2007-04-04
You havn't mentioned resizing an existing partition, defragmenting, and running CHKDSK, so have you?

---

### Post by Kanybus on 2007-04-04
I ran Perfectdisk 7 yesterday for the defrag a few hours before I tried to install.  I'm trying to resize my existing windows partition but haven't done a chkdsk yet so:

Yes
Yes
No

---

### Post by mikewhatever on 2007-04-04
When I tried to install 6.10 a few month ago, I was supprised to discover I could not shrink the Windows partitions on the SATA HDD of the HP Pavilion 5000 laptop. I used the altarnate installer, not the desktop, and there was no error message of any kind, but the partitionner wouldn't do anything. Then, I got a GPated live CD, which is a newer version of the partitionning program on Ubuntu live CDs, and it showed an error in one of the menus, specifying I had to run CHKDSK. After having done that from Winows, the resizing took about 10 secs.

I'd suggest running CHKDSK check and trying Ubuntu cd partitionner again. If it does not work, get the newest GParted live cd.

---

### Post by Kanybus on 2007-04-05
Ya I ran a chckdsk and still no install.  My friend gave me a few ideas since he's the one that got me into ubuntu then I'll try your thing.

---

### Post by LaurelLynn on 2007-04-05
Dear Kanybus,

I had a similar problem when I did my install. Gparted just keep locking up.  The way a got it to work was to move the /swap partition to the last partition. I had originally had it partitioned between the /root and /home partitions.

The only explaination that comes to mind, is that the /swap partition has block alignment needs that prevented it from starting at the original location.

To repartition I ended up having to boot window to erase the /swap partition (oh the shame). That is because all my Live CDs kept mounting the /swap partition for their own use and wouldn´t give it up. I´m sure someone else here  knows how to release it while linux is running.

Laurel Lynn

---

### Post by indytim on 2007-04-05
Highly recommend:

1.  Doing the HD cleanup as described above.
2.  Run GParted Live and pre-configure your partitions needed for install ( min ext3 for "/" and a swap partition (2x RAM).
3.  Run your installer and do the manual configuration of partitions.  Identify the partitions created in #2 (make sure you check the "format" option for "/" and swap.

I've done this successfully across 9 different Linux ops installs in the last 2 years. My most recent install was 4-Apr-2007 with Kubuntu 7.04.

 Oh, and btw - I'm running SATA HDs.

IndyTim

---

### Post by Sef on 2007-04-05
You might want to try [GParted]("http://gparted.sourceforge.net") itself.  It is newer than what is on Ubuntu.

---

