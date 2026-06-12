---
title: "Old Win Partitions"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by guasano on 2007-01-11
I got a hand-me-down computer from a roommate a few months ago.  He was having trouble (running MS Win2000) that wasn't worth fixing in his rather wealthy reasoning, so he gave it to me.  Some error occurred and part of the boot sequence was deleted.  I installed Dapper Drake and have fallen in love with it.  I just opened Disks Manager (just one hard drive 120 GB) and noticed some music and other data (school papers, etc) in partitions 1 and 2.  Partition 3 (only 20 GB) has all Ubuntu stuff and is nearly full.  When I try to Browse Partion 1 or 2 I get the following message:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-hdb1".

If I then go "Up" I can see the folders disks-conf-hdb1 and disks-conf-hdb2 (both locked), which are both found in my tmp folder.

So, finally the question:

Can I retrieve data from previously created partitions made in Win2000?
then, Can I remove those partitions and create new ones?

Still getting the hang of things with Linux, thanks for your help.

---

### Post by taurus on 2007-01-11
You need to mount it with a read permission that this guide should help.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by b_martinez on 2007-01-11
> **guasano said:**
> I got a hand-me-down computer from a roommate a few months ago.  He was having trouble (running MS Win2000) that wasn't worth fixing in his rather wealthy reasoning, so he gave it to me.  Some error occurred and part of the boot sequence was deleted.  I installed Dapper Drake and have fallen in love with it.  I just opened Disks Manager (just one hard drive 120 GB) and noticed some music and other data (school papers, etc) in partitions 1 and 2.  Partition 3 (only 20 GB) has all Ubuntu stuff and is nearly full.  When I try to Browse Partion 1 or 2 I get the following message:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of " disks-conf-hdb1".

If I then go "Up" I can see the folders disks-conf-hdb1 and disks-conf-hdb2 (both locked), which are both found in my tmp folder.

So, finally the question:

Can I retrieve data from previously created partitions made in Win2000?
then, Can I remove those partitions and create new ones?

Still getting the hang of things with Linux, thanks for your help.

Yes, it's possible to view/recover the info on those partitions. I'm not sure if you need ntfs-g3, which will allow you to read/write to ntfs partitions.
Open a terminal and type in this,[each line followed by hitting the enter key]
```
sudo mkdir /media/disks-conf-hdb1
[enter your password here]
mkdir /media/disks-conf-hdb2
chmod 777 disks-conf-hdb1
chmod 777 disks-conf-hdb2
mount /dev/hdb1 /media/disks-conf-hdb1
mount /dev/hdb2 /media/disks-conf-hdb2
```
If this doesn't allow you to read/copy these partitions, then you will need to install ntfs-g3 [I think it's called that]. _How_ to do that is something you will need someone else to help you with.
hth
Bill

---

### Post by guasano on 2007-01-11
I tried the instructions at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), however my /etc/fstab file does not have any indication of either of the partitions:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The partitions are certainly NTFS:

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        6374    51199123+   7  HPFS/NTFS
/dev/hdb2            6375       12090    45913770    7  HPFS/NTFS
/dev/hdb3   *       12091       14825    21968887+  83  Linux
/dev/hdb4           14826       14946      971932+   5  Extended
galen@galen-desktop:~$ 26       14946      971901   82  Linux swap / Solaris

So I don't suppose I should add a line as I would with a FAT32 partition?

---

### Post by taurus on 2007-01-11
From a terminal, Applications -> Accessories -> Terminal, edit your /etc/fstab with

```
gksudo gedit /etc/fstab
```
Now, add these two lines to the end of it.

```

/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb2   /media/hdb2   ntfs   nls=utf8,umask=0222   0   0

```
Save the changes and now, create two new mount points and mount them.

```
sudo mkdir /media/hdb1 /media/hdb2
sudo mount -a 
df -h
```

---

### Post by guasano on 2007-01-11
1 million thanks to you, taurus!  worked like a charm after I created the new mount directory.  if only every group of people was as helpful as the linux community!  thanks again. \\:D/

---

### Post by taurus on 2007-01-11
> **guasano said:**
> 1 million thanks to you, taurus!  worked like a charm after I created the new mount directory.  if only every group of people was as helpful as the linux community!  thanks again. \\:D/

You're welcome.

---

### Post by disophisis on 2007-02-21
This worked perfectly, this is only my second day on Ubuntu, and some of the lingo was confusing, but <5-10 minutes I was able to access a whole 160 gig hard drive that had been locking me out

Thanks a lot.

---

### Post by guasano on 2007-02-21
Isn't Ubuntu great?

---

### Post by punx45 on 2007-02-21
now what I would do is save anything from the drive that you need/want like music or any files that the roomate might want to keep, (burn it onto discs or transfer to external HDD or another computer)  then before you get too settled, wipe the drive and reinstall onto a roomy disk with 160GB usable rather than being holed up in 20GB.

---

