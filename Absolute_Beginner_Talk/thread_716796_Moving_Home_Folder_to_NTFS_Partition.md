---
title: "Moving Home Folder to NTFS Partition"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2008-03-06
Hey guys,

I have dual booted my laptop with Microsoft XP Home Edition and Xubuntu Gusty Gibbon 7.10 on two separate partitions.  I have a third partition formated as NTFS to store all my data on and to be able to access from both Windows and Xubuntu (I understand that Gusty Gibbon can now read/write to NTFS partitions?)

My question is, how do I move my /home folder to the NTFS partition?

---

### Post by taurus on 2008-03-06
Moving /home to ntfs filesystem should not be done at all cost because it will break your machine, not allowing you to log in again.

---

### Post by mikeypc2006 on 2008-03-06
Why would it break my machine when Xubuntu is able to read/write to NTFS partitions?

---

### Post by taurus on 2008-03-06
It's because ntfs filesystem doesn't play nice with permissions and ownerships.  And if you don't believe it, back up your important files from your $HOME first and go for the migration.  You will find out as soon as the next time you try to log in.

---

### Post by mikeypc2006 on 2008-03-06
So then how do you suggest I should partition my PC so that I can share my data between Linux and Windows so that if something happens to either Linux or Windows, I don't loose all my data if I have to reformat one of the OS partitions?

---

### Post by taurus on 2008-03-06
Just create an extra partition and format that as ntfs.  Then, mount it to somewhere like /media/share in Ubuntu and share that partition with your windows.  And just so you know, you can access Ubuntu partition(s) from XP if you install fs-driver first.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jken146 on 2008-03-06
Leave home where it is, but put the files you want to share on that NTFS partition.  You can mount it as /media/storage or similar.  See [www.psychocats.net.ubuntu/mountwindows](www.psychocats.net.ubuntu/mountwindows) for a guide.

---

### Post by spklr246 on 2008-03-06
Yeah, I would also recommend not moving /home - IMO if you want to be able to share data between partitions your safest bet is to manually copy the files that you want to share over to the windows partition.  You could probably even create a symlink to the NTFS drive in  /home/<user>/, so instead of copying over just save them in the symlink-ed folder.

---

### Post by mikeypc2006 on 2008-03-06
Would I be better having the data partition as ext3 rather than NTFS?  Is there anything I can install in Windows to get it to read ext3 partitions?

---

### Post by sisco311 on 2008-03-06
> **mikeypc2006 said:**
> Would I be better having the data partition as ext3 rather than NTFS?  Is there anything I can install in Windows to get it to read ext3 partitions?
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mikeypc2006 on 2008-03-06
> **sisco311 said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)

That seems like a good solution to me, thanks :)

Would I then be able to move the /home folder onto the separate ext3 partition?

How can I go about formatting the NTFS partition as ext3?  Could I use GParted?  How do I install gparted and how do I go about getting it to change the partition from NTFS to ext3?

---

### Post by guilly on 2008-03-06
> **mikeypc2006 said:**
> That seems like a good solution to me, thanks :)

Would I then be able to move the /home folder onto the separate ext3 partition?

How can I go about formatting the NTFS partition as ext3?  Could I use GParted?  How do I install gparted and how do I go about getting it to change the partition from NTFS to ext3?

open terminal -> sudo apt-get install gparted 


that will install gparted, then from there you should be able to format to ext3. Another option would be to format to FAT Windows and Linux can both read this format. However, there may be performance issues regarding FAT it is an old format, I'm not 100% sure how it would affect you performance wise if any at all.

---

### Post by mikeypc2006 on 2008-03-07
Once I've formatted the partition as ext3, how do I then go about moving the /home folder to the partition?

---

### Post by dcstar on 2008-03-07
> **mikeypc2006 said:**
> Once I've formatted the partition as ext3, how do I then go about moving the /home folder to the partition?

There are HOWTOs on this with detailed instructions, do a search for them.

---

### Post by bodhi.zazen on 2008-03-07
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by mikeypc2006 on 2008-03-09
It's all up and working as I would expect, thanks guys :)

However, what happens when I upgrade Xubuntu for example to 8.04 or if I do a new clean install of Xubuntu?  Will the new installation know about the /home folder on the separate partition or will I have to teach it again?

---

### Post by bodhi.zazen on 2008-03-10
Upgrade should be no problem.

If you fresh install, during the install mount the partition at /home WITHOUT formatting it.

---

### Post by mikeypc2006 on 2008-03-13
> **bodhi.zazen said:**
> Upgrade should be no problem.

If you fresh install, during the install mount the partition at /home WITHOUT formatting it.

How and when would I mount the partition at /home during a fresh installation?

Without Linux, would Windows still be able to read the Ext3 partition?  The reason I'm asking, when I failed to load up Xubuntu correctly, I booted Windows and it could no longer see the partitions.  When I restarted Xubuntu and ran it correctly and loaded back into Windows, the partitions were back.

I don't want to format the Xubuntu partition and suddenly find that I've lost access to the other partition with /home on in Windows!

---

### Post by bodhi.zazen on 2008-03-13
> **mikeypc2006 said:**
> How and when would I mount the partition at /home during a fresh installation?

As you install, at the partitioning section, select manual partitioning, set the mount point of your home partition to /home, do not format it ...

> Without Linux, would Windows still be able to read the Ext3 partition?

If you installed the fsdriver on Windows you can read ext2 or ext3 from Windows. It is a windows thing not a linux thing.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

> The reason I'm asking, when I failed to load up Xubuntu correctly, I booted Windows and it could no longer see the partitions.  When I restarted Xubuntu and ran it correctly and loaded back into Windows, the partitions were back.

Not sure what happened there ...

> I don't want to format the Xubuntu partition and suddenly find that I've lost access to the other partition with /home on in Windows!

I do not think that will be a problem ...

---

