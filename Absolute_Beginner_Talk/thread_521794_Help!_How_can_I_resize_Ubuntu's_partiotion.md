---
title: "Help! How can I resize Ubuntu's partiotion?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by cursebg on 2007-08-09
Hi,
I've installed Ubuntu on 5,8 GB volume, but now I'm short of space for it! The rest of my drive is empty and I want to enlarge Ubuntu to about 20 GB.
Is this possible? It should be or it would be the first thing I can't do under it :)

---

### Post by bren on 2007-08-09
1) back up data that is needed

2) start System-Administration-Gnome Partition Editor

(if it is not there then sudo apt-get install gparted)

3) use gparted to resize the partition (right click on relevant partition and change size)

bren

---

### Post by toidi on 2007-08-09
I believe that you can boot into the livecd and then use the gnome partition manager to make your partition bigger.

I tried this and it would not let me do it, but after a couple of days of fiddling around with things and a LOT of reading I managed to create a second partition and claim ownership of it.  This allowed me to store most of my stuff on the new 'data' partition without any problems at all.

Hope this helps..

---

### Post by cursebg on 2007-08-09
> **bren said:**
> 1) back up data that is needed

2) start System-Administration-Gnome Partition Editor

(if it is not there then sudo apt-get install gparted)

3) use gparted to resize the partition (right click on relevant partition and change size)

bren

Thanks, but... what do I have to to backup if i want to save my VPN settings? I walked through hell to get it working... 
and what's the chance to succeed? I mean the rest of the HD is unallocated, could there be a problem at all??

---

### Post by cursebg on 2007-08-09
> **toidi said:**
> I believe that you can boot into the livecd and then use the gnome partition manager to make your partition bigger.

I tried this and it would not let me do it, but after a couple of days of fiddling around with things and a LOT of reading I managed to create a second partition and claim ownership of it.  This allowed me to store most of my stuff on the new 'data' partition without any problems at all.

Hope this helps..

It does help. Now I got riid of the idea to use the installed Ubuntu to resize :)

I'm dual booting with XP and I have Partition Magic. Is it safe to use it?

---

### Post by toidi on 2007-08-09
I had vista and ubuntu on the same drive.  I used the gnome partition mananger to create a 20 gig partition using the reiserfs 3 file system.

Worked a treat but I soon ran out of space.  So I booted to the live cd again to increase the partition, it wouldn't let me.

I created another reiserfs partition using the gnome partition manager, it worked but still would not let me resize my original partition to incorporate the new partition.

So I decided to get ubuntu to automount the partition at startup and then I realised that I would have to claim ownership of the partition in order to use it properly.

This is how I did it.

First I searched for my new partition in the console

sudo fdisk -l (the l is a small L)

I got the following results

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       10738    86251961    7  HPFS/NTFS
/dev/hda2   *       16271       19458    25600000    7  HPFS/NTFS
/dev/hda3           10739       16270    44435790   83  Linux

*note that hda3 is my new partition.

I then did the following.

sudo mkdir /media/hda3  (this is in ubuntu 7.04 and I used the same name as my partition as not to confuse me later).

I then edited the fstab file so that ubuntu will automount the new partition on boot.

sudo gedit /etc/fstab

at the bottom of the file I wrote the following command and saved out.
/dev/hda3    /media/hda3 reiserfs notail 0 1

That mounted my new partition on boot.

Reboot or do a sudo mount -a

Now all I had to do was take control of it so that I could store files and execute them.

sudo chown cheese:cheese /media/hda3 (cheese is replaced by your default username and the second cheese is replaced by your default user group (also your default username if you have not messed about with it).

Just what I did, not sure if all the syntaxes are correct or there is an issue here.  But it let me access and control another partition to use for my data.

Cheers toi..

---

