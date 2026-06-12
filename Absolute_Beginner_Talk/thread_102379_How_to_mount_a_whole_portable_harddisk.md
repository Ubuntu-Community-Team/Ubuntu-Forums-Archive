---
title: "How to mount a whole portable harddisk?"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Dislimit on 2005-12-11
How to mount a whole portable harddisk?
Actually I'm using an IDE harddisk as a portable harddisk.

---

### Post by LoclynGrey on 2005-12-11
portable as in USB connection?
fat32 or NTFS partition?

---

### Post by yapsuper on 2005-12-11
I have a bit experience and you do need to answer loclyn's question first. If its NTFS then linux won't be able to write to it. you want to format it as a fat 32 which windows can do if its not great than 36 gb. If it is then do what I did and ask some mac user to format it for you. 

To mount such a disk open up te terminal and use this code
```
su mount /dev/sda1 /foobar
```
where foobar is where you want the device to show up. Also replace sda1 with what your hard disk is recognized as. If its a usb connection it will be sd and if its the first drive to be plugged then an "a" will follow it and then type the number partition you want to mount. hence the sda1. Don't forget to unmount your disk

```
su umount /dev/sda1
```

I hope I'm not completely off the mark with you question

---

### Post by Dislimit on 2005-12-11
Thanks, yapsuper. But still some problems.

Here is the situation:
1. I have 4 partitions in this disk, three NTFS and one FAT32 which is more than 40GB large. I wanna fetch something from the large FAT32 partition.
2. I connect this IDE harddisk with a transport cable. Linux can detect the disk but there is only an sdb in /dev. (Since I'm using a T43, the sda is my own harddisk. It is interesting that my current hard disk is an sd, while my extension disk now should be an hd. :-) )

---

### Post by Dislimit on 2005-12-11
Thanks, yapsuper. But still some problems.

Here is the situation:
1. I have 4 partitions in this disk, three NTFS and one FAT32 which is more than 40GB large. I wanna fetch something from the large FAT32 partition.
2. I connect this IDE harddisk with a transport cable. Linux can detect the disk but there is only an sdb in /dev. (Since I'm using an IBM T43, the sda is my own harddisk. It is interesting that my current hard disk is an sd, while my extension disk now should be an hd. :-) )

---

### Post by yapsuper on 2005-12-11
Try cat and see if linux truly registers your drive```
cat /etc/sysconfig/hwconf
```

---

