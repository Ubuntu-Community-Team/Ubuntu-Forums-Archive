---
title: "mounting ntfs hard drive"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by scoldingice on 2005-10-15
i know this is a topic thats been posted before i just dont understand what i'm supposed to do.

ok i have a 30 gig hard drive that is partintioned in two. one side is for windows xp and programs and the other side is for music. now i have ubuntu running on a lil 4 gig hard drive. sry if this is confusing.

now i want to mount the second half of my 30 gig HD.
i have used this comand "/dev/hda2 /mnt/windows ntfs users,umask=0222,auto,ro 0 0" 
but i keep geting permission denied. someone please help me

---

### Post by aysiu on 2005-10-15
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by scoldingice on 2005-10-15
ok i got it mounted but nothing showed up. how am i suppose to access it?

---

### Post by The Headhunter on 2005-10-15
does it not show up on the desktop or under the Places menu?

---

### Post by scoldingice on 2005-10-15
nope not at all

---

### Post by The Headhunter on 2005-10-15
Just to make sure it's not there at all, go to the /media directory.  If it mounted correctly, it should be there.

---

### Post by aysiu on 2005-10-15
If you followed the directions I linked to, it should be in the /media/windows folder. You may need to reboot to have the changes take effect (there's another way to do it without rebooting, but rebooting's simpler).

---

### Post by scoldingice on 2005-10-15
ok i see windows but i cant ged the second partition to mount

---

### Post by aysiu on 2005-10-15
When you click on the windows folder, the partition should be in there. It's a partition, but it should appear to be a regular folder, as if it exists within Ubuntu.

---

### Post by scoldingice on 2005-10-15
nope just normal windows folders

---

### Post by aysiu on 2005-10-15
[QUOTE=scoldingice]nope just normal windows folders[/QUOTE] That's what should be there--normal Windows folders. I'm confused. I don't know what you're trying to do. My Windows partition is mounted at /xp, so when I navigate to the /xp folder, [this](http://i22.photobucket.com/albums/b337/psychocats/010ad02c.png) is what I see. Those are "normal Windows folders," but that's what I wanted.

Again, I'm not sure what you're trying to accomplish.

---

### Post by scoldingice on 2005-10-15
ok on my 30 gig hd i have two partitions one for windows and one for music. i want to access the second partition that has the music.

---

### Post by jasay on 2005-10-15
It sounds like you only mounted the first partition.  You have to mount each partition seperately.  

If you mount the first parition like this 
```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222
```

Then you have to change a few things for the second partition.  Notice the change from hda1 to hda2 showing that it is the 2nd partition on the same hard drive ( hard drive a).  You'll also have to call it something different like "music"  or "media" since that seems appropriate for your files.
```
sudo mount /dev/hda2 /media/music/ -t ntfs -o umask=0222
```

---

### Post by scoldingice on 2005-10-15
ok i did that and this is what i got 

root@brian-ubuntu:/home/moneyman # sudo mount /dev/hda2 /media/music/ -t ntfs -o umask=0222
mount: mount point /media/music/ does not exist

---

### Post by jasay on 2005-10-15
Sorry about that.  You have to make the folder first before you can mount the partition there.  Try ```
sudo mkdir /media/music
``` and then remount.

---

### Post by scoldingice on 2005-10-15
um ok i got this this time

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by jasay on 2005-10-15
Hmm.  One last question and then I'm in over my head.  Is the music partition formatted in NTFS or FAT32?

If you don't know go to System->Administration->Disks and click on your hd on the left and then the partitions tab.  It should list the filesystem type there.

---

### Post by scoldingice on 2005-10-15
o s**t i forgot (sheepishly) um ya its in fat32.

---

### Post by jasay on 2005-10-15
This *should* mount it then with read/write capability.
```

sudo mount /dev/hda2 /media/music/ -t vfat -o umask=000
```

---

### Post by scoldingice on 2005-10-15
omg i'm gonna cry it did the same thing.

---

### Post by jasay on 2005-10-15
Then only other thing I can say is that you might check the disk manager and make sure that there are two partitions and they are in fact /dev/hda1 and /dev/hda2 (can't think of what else they would be since you seem to have mounted windows ok).  Just to make sure we're not trying to mount some crazy windows recovery partition that they never tell you about or something (although that should work too:( ).  But otherwise, hopefully someone who knows a little more can help.

---

### Post by scoldingice on 2005-10-15
ok well thanks for your help. hey we got the windows one mounted so thats a step in the right direction.

---

### Post by aysiu on 2005-10-16
If you type ```
sudo fdisk -l
``` into a terminal, it'll display your partitions and their respective types. For example, when I type it in, I get this: ```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       18494   133202947+   f  W95 Ext'd (LBA)
/dev/hda3           18495       19457     7735297+  83  Linux
/dev/hda5            1912       14763   103233658+   b  W95 FAT32
/dev/hda6   *       14764       16434    13422276   83  Linux
/dev/hda7           18363       18494     1060258+  82  Linux swap / Solaris
/dev/hda8           16435       18362    15486628+  83  Linux

Partition table entries are not in disk order

```

---

### Post by scoldingice on 2005-10-16
omg thankyou that showed me that it was listed as hda5 thankyou so much. and thankyou to everyone who  helped me.

---

