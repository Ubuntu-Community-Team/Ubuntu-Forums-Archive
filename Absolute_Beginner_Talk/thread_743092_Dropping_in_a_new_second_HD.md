---
title: "Dropping in a new second HD"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by rayj on 2008-04-02
OK...

I looked around, but couldn't find an answer to my problem. It's a simple one: I just dropped in a second hard drive (a SATA 3.0, exactly the same as my main disk). I partitioned everything on the new drive (ext3, same as hd0). The partitions are located in /dev/sda/ for the original, and /dev/sdb/ for the new partition. The new disk shows up in GParted, but as unmounted...

How do I mount the new partition? Is it as simple as sudo mount /dev/sdb/?

Another question: I'm seeing some paths referencing IDE drives. I'm presuming these are paths to the DVD-R drive and whatnot, but I don't remember the partition editor asking if my new drive is an IDE or a SCSI drive...my main drive is mounted as a SCSI (SATA 3.0). Do I have to do something to run the new drive as a SCSI?

If it helps, my use for the new drive is for multitrack audio files...

Thanks, and please excuse the ignorance of this newbie...

---

### Post by taavikko on 2008-04-02
You have to edit /etc/fstab to mount it automatically.

you can always mount it using sudo mount /dev/sdX /mount/point/
but it wont stay mounted over reboot.

---

### Post by aeiah on 2008-04-02
if it is pretty similar to your other hard drive, you can edit fstab by copying the information for sda and changing the applicable bits for sdb. to manually mount do what was mentioned, ie:

sudo mount /dev/sdb /media/mountpoint

make sure you have created the mount location first though:

sudo mkdir /media/mountpoint

---

### Post by rayj on 2008-04-02
Thanks for the prompt answers! I love this place...

I followed the commands, and ended up here:

rayj@prime:~$ sudo mount /dev/sdb /media/mountpoint
mount: unknown filesystem type 'promise_fasttrack_raid_member'

Huh? I don't quite get it...I formatted the filesystem as ext3...

However, when I look at the partition in Gparted, I see two partitions...an extended partition with an 'embedded' ext3 partition...both partitions of the same size (the usable size of the disk). I don't quite grasp the principle at work here...does the 'extended' partition allow the kernel to see sdb as space on the main system drive (doesn't seem likely...), or was my poorly-educated decision to format it that way wrong?

---

### Post by bumanie on 2008-04-02
I am no expert on fstab, but 
Before continuing, you should read this to undestand fstab and what a mountpoint is; basically / or /home or /media/cdrom or /media/fd0 etc. [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
Hope this helps. Post again if you need further assistance after reading the above, post again. If you want to mount the drive at boot, edit fstab according to the rules in 'tuxfiles'.
Before editing, backup fstab (as below), so that if you make errors you can revert to your present list.
> sudo cp /etc/fstab-backup /etc/fstab 
To get fstab to edit
> sudo gedit /etc/fstab

---

### Post by taavikko on 2008-04-02
> **bumanie said:**
> I am no expert on fstab, but 
Before continuing, you should read this to undestand fstab and what a mountpoint is; basically / or /home or /media/cdrom or /media/fd0 etc. [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
Hope this helps. Post again if you need further assistance after reading the above, post again. If you want to mount the drive at boot, edit fstab according to the rules in 'tuxfiles'.
Before editing, backup fstab (as below), so that if you make errors you can revert to your present list.


Quote:
sudo cp /etc/fstab-backup /etc/fstab
To get fstab to edit
Quote:
sudo gedit /etc/fstab

To get fstab to edit

NOOOO!!!!

If you backup anything it's
```
sudo cp /etc/fstab /etc/fstab.backup
```
Not the other way around!
when you want the older back its
```
sudo cp /etc/fstab.backup /etc/fstab
```

---

### Post by wolfen69 on 2008-04-02
add to fstab:
```
/dev/sdb1 /media/mountpoint  ext3 rw,auto,user,exec 0      0
```
position cursor at the end of that line and hit enter. then save. now try and mount.

---

### Post by bumanie on 2008-04-02
OOps Sorry. Glad you were on the ball!
Do this
> sudo cp /etc/fstab /etc/fstab.backup
not as first put. Sorry again.

---

### Post by Duck2006 on 2008-04-02
This guide may help to.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by rayj on 2008-04-02
Thanks again all...

Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bdeba473-e725-4efe-8b01-fa53de797837 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5

UUID=61eb9cdf-9f70-4cfb-a2a4-647feddc21eb none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


There is some odd sda5 partition...did I somehow 'extend' my hda partition across hdb? Excuse me, as I'm on lunchbreak, and don't have time to read the links this second. Ignore the above if those links handle my problem...

Quoted from my earlier post:

However, when I look at the partition in Gparted, I see two partitions...an extended partition with an 'embedded' ext3 partition...both partitions of the same size (the usable size of the disk)

it shows sdb1 as a full-size extended partition, with sdb5 as an ext3 partition...with the same (full) size as the extended partition, 'nested' within the full-size sdb1 partition. Hmm.

---

### Post by rayj on 2008-04-03
Issue resolved! Thanks to everyone for the guidance. Now I just have to modify all the permissions...

---

