---
title: "Order of mounting removable drives"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by dwiedenfeld on 2007-11-29
I have a USB flash drive partitioned into four fat32 primary partitions. 

When I plug in the flash drive, all four mount automatically just fine. No problem there.

However, they seem to mount in random order. That is, one will get the name "disk", one will get "disk-1", one will be "disk-2", and the last will be "disk-3", and it's never the same order.

OK, this may not be the biggest problem there is, but it makes it hard to find a file. Since I don't know what the name of the disk will be, I have to look at each one until I can identify it.

So, I have two questions: Can you control the order that the four drives mount? That is, could I force Ubuntu to mount partition 1 first, number 2 second, etc., so that at least I would always know that, say, "disk-2" is the third partition?

Or is there a way to name the partitions with a permanent name, so that it shows up each time they are mounted, and I could tell them apart no matter what order they mount in? In Windows this name is called  something like "volume name".

By the way, this seems to happen the same way on my desktop with Ubuntu Feisty and on my laptop with Xubuntu Gutsy.

---

### Post by nixx on 2007-11-29
you could modify your /etc/fstab file to mount the drives by UUID, so that you can set specific mount points for the individual drives. I'm not sure how well this would work for automounted drives, but i assume it would work just fine.

---

### Post by dwiedenfeld on 2007-11-29
> **nixx said:**
> you could modify your /etc/fstab file to mount the drives by UUID, so that you can set specific mount points for the individual drives.

Sorry, I'm here on "Absolute Beginner Talk" for obvious reasons: 

So how do I do that? First, how do I determine the UUID? 

It actually seems to me that it would be easier just to give each drive a name. I know this can be done, because it can be done in Windows. But how do you do it in Ubuntu?

---

### Post by Inxsible on 2007-11-29
you can get the UUID, by using the following command:
```
ls /dev/disk/by-uuid -lah
``` The UUID will be a long alphanumeric number. I would suggest that you label each of the partitions and use that instead, because they will be meaningful to you.
You can use e2label to give labels to the drives.

Go to the Understanding fstab link in my signature for a great how to.

---

### Post by nixx on 2007-11-29
okay so first of all plug in your usb drive. then run Inxsible's command.
```
ls /dev/disk/by-uuid -lah
```

that will print out a list of UUIDS for your drives. You'll need to note the UUIDs for the specific drives you're talking about, so maybe run this command without your drive in, and then plug it in and run the command again, the new entries are the ones we need.

Now this detail is what we need to add to the file /etc/fstab. So store this info in a text file somewhere maybe, then remove your drive.

Run
```
sudo gedit /etc/fstab
```

In this we're going to create new entries for your drives to mount into.
We need to add a new line to this file which will be as follows --

```
UUID=HERE    MOUNTPOINT     ext3     defaults,errors=remount-ro    0      1
```

Replace HERE with the UUID of the partition, replace MOUNTPOINT with where you want the drive to mount to every time (remember that this location must exist for it to be allowed to mount to it, so ensure you create the folder first [maybe /media/usb-partition1 ?] and then enter the exact location here. The rest you shouldn't need to worry about. 

You'll need to do this for each of your 4 partitions to make sure they all mount in the same locations. Any problems post again.

---

### Post by dwiedenfeld on 2007-11-29
Great! Thanks very much to both of you (nixx and inxsible) for very useful and clear responses. I'll give them a try.

---

### Post by dwiedenfeld on 2007-11-29
I should point out that e2label in inxsible's message is only for ext2 or ext3 partitions, while mine are all fat32. 

However, also in inxsible's message is a link to the fstab how-to, which does explain how to label the volumes, using mtools.

---

### Post by vanadium on 2007-11-29
Don not edit fstab! Removable drives in Ubuntu are normally not mounted through /etc/fstab. To make sure your partitions are mounted with a distinct name, change the volume labels of each of the partitions. The easiest way to do that for a fat partition is probably using ms-windows. Under Linux, it can be done using the mtools. See here [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

When following forum advice, be always very critical and verify the advice.

---

