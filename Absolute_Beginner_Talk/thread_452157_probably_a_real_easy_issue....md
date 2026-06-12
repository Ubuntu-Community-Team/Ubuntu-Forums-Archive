---
title: "probably a real easy issue..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by nepheal on 2007-05-23
Alrighty... So if you haven't guessed I'm about as new as a young babe to Ubuntu, and as I'm sure you're also going to see / point out is a thread that I haven't seen. true enough, I've had a quick glance and haven't come to see the area that I've needed. Anyway, I'll get to the point then.

As it stands I just installed Ubuntu 7.04 (i think) to my computer, on a 250 GB HDD partitioned previously with win XP home to be 50 GB / 200 GB. I usually use the 50 GB partition for random attempts of going outside what I know, in this instance, Ubuntu. So anyway, I loaded the 50 GB partition with Ubuntu as I belive jfs and the other 200 GB partition as a swap drive. All looked ok to me, but when I loaded up my computer, low and behold I couldn't access my 200 GB partition. Any help towards what's probably a very simple issue? Thanks :)

Alrighty, that was posted just moments ago in "the beginner team has started" thread... as for sudo fdisk -l, the output is this:


```
matt@matt-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+  82  Linux swap / Solaris
/dev/sda2           25497       30400    39391380    f  W95 Ext'd (LBA)
/dev/sda5           25497       30400    39391348+  83  Linux
```


oh, and yes, I did setup the 200 GB partition as swap... it sounded right to me, then again till now I'v been a total windows user, figure I'd just make the jump to linux before  I forget about it :(

---

### Post by Fiyastone on 2007-05-23
The swap file is used by the system as 'virtual memory'.  its not accessible by the user directly.  A recommened size for your linux-swap would be 1.5x your physical RAM amount, capping out at 2 GB. 

You will have to re-partition your disk to make that partition smaller into a ~2 gb linux-swap and a ~198 gb ext3 file system.

I am not sure off-hand how to re-partition inside of Ubuntu, but I use a live cd program called gparted.   Its the same gnome partition manager that ubuntu uses to set up the partition tables, and it has a wonderful GUI to play around with your hard disks.

---

### Post by nepheal on 2007-05-23
well, what my intention was, is to setup a spare drive, or slave drive for better wording for linux. i'm so use to doing it with windows and I have no idea how it's done with linux. All I really do know, is that it's sad that I've memorized the key strokes for reformatting a windows pc... (enter -f8 -esc-del-enter-l-c-enter-enter-up-enter).... one reason why I made the jump to linux

---

### Post by Inxsible on 2007-05-23
If you recently installed Ubuntu , you probably havent done much with it. Try installing it over again. 

This time however, try following these guides :

[www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing)

and

[www.psychocats.net/ubuntu/partitioning](www.psychocats.net/ubuntu/partitioning)

---

### Post by drowner on 2007-05-23
Nepheal: 

1. It appears your windows is gone. The whole windows drive is now 'swap'

2. In theory your system should be FLYING. ;)

Think of swap as 'virtual RAM'. You now have 200 gig of virtual ram.

Was your intention to completely remove windows?

---

