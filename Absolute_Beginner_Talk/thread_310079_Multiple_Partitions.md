---
title: "Multiple Partitions"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by mrthi3f on 2006-11-30
Although I am not new to Ubuntu I am new to the setup that i have right now.  I installed ubuntu on a very old computer (no name brand) after putting in an extra 20 gig hard drive i had laying around.  After I installed I found that when i went to boot grub failed because the computer was so old it couldn't handle a boot of more then a 4 gig partition.  So i partitioned the harddrive with a 3...... gig boot 140 mb swap and was left with a 17 gig free space part.  My question is how do i get the 17 gig part to show up in Ubuntu.

Thanks in advance :)

---

### Post by CatKiller on 2006-11-30
Use GParted (in the [repositories]("http://monkeyblog.org/ubuntu/installing/"), on the install disc, or on the [GParted live cd]("http://gparted.sourceforge.net/livecd.php")) to make a new ext3 partition, and then [mount it into your filesystem]("http://www.psychocats.net/ubuntu/index.php").

---

### Post by bulldog on 2006-11-30
Is there a possibility to upgrade your BIOS?
This should be the most simple way to handle things.
When your BIOS can't handle a partition biggers as 4GB,I'm afraid Ubuntu can't either.

But have to say I'm not very sure about this.
You can try to mount the 17GB partition in Ubuntu.
```
sudo mkdir /mnt/data
```
You can mount were ever you want and make a mount point were ever you want,this is just an example.
To mount you have to know how the partition is listed.
```
sudo fdisk -l  (l as in like)
```
Now mount the partition,
```
sudo mount /dev/hda? /mnt/data
```
hda? stands for what you found with fdisk -l.

---

### Post by userundefine on 2006-11-30
> **mrthi3f said:**
> So i partitioned the harddrive with a 3...... gig boot 140 mb swap and was left with a 17 gig free space part.
You do mean 3GB / partition, don't you?  There's no reason for a 3GB /boot partition.

---

### Post by Zaen on 2006-11-30
> **bulldog said:**
> Is there a possibility to upgrade your BIOS?
This should be the most simple way to handle things.
When your BIOS can't handle a partition biggers as 4GB,I'm afraid Ubuntu can't either.

But have to say I'm not very sure about this.
You can try to mount the 17GB partition in Ubuntu.
```
sudo mkdir /mnt/data
```
You can mount were ever you want and make a mount point were ever you want,this is just an example.
To mount you have to know how the partition is listed.
```
sudo fdisk -l  (l as in like)
```
Now mount the partition,
```
sudo mount /dev/hda? /mnt/data
```
hda? stands for what you found with fdisk -l.

I had an old laptop where the bios wouldn't boot anything over 8 gigs. All I had to do was make a small boot partition ( around 100 megs ) and install ubuntu under the rest of the space.

---

### Post by mrthi3f on 2006-11-30
> **userundefine said:**
> You do mean 3GB / partition, don't you?  There's no reason for a 3GB /boot partition.

I need the 3 GB partition so the computer can boot since the bios is so old. I'm currently trying to Gpart the hard drive

---

### Post by LLRNR on 2006-11-30
> **Zaen said:**
> I had an old laptop where the bios wouldn't boot anything over 8 gigs. All I had to do was make a small boot partition ( around 100 megs ) and install ubuntu under the rest of the space.

Zaen is right... If your BIOS can only boot a very small partition, then in GParted you have to make (mainly) 3 partitions: 1 for swap (your RAM amount * 2), 1 for /boot (around 32 MB, it doesn't need more) and 1 for / (the root of your filesystem). You could also make a 4th partition for your /home directory, but although it's recommended you're not obliged to do it. And then things should be ok, since your BIOS will boot from the 32 MB partition, the one mounted under /boot...

LLRNR

---

### Post by mrthi3f on 2006-12-01
I would like to thank you all esp. Bulldog for the help.  I have my partitions working and Ubuntu is ready to go!

---

