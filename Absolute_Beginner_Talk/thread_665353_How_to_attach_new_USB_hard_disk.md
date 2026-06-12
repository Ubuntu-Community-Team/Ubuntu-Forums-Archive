---
title: "How to attach new USB hard disk?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by johann_p on 2008-01-12
Is there a HOWTO or some documentation anywhere how to attach a new USB harddisk to my computer?

Obviously the necessary steps would involve:
* reformatting the harddrive so that instead of VFAT it is Reiser or EXT2
* managing how the drive will be mounted (mount point, permissions etc) when it is connected to the computer

So what is the recommended way to do this? Is there a GUI that suports these steps?

---

### Post by fiddledd on 2008-01-12
You may want more detail than I can give but this is all I did:

Connected the Drive to PC
Run Gparted and created partitions and formatted to ext3
Nothing else :)
Ubuntu sees the Drive and I can read/write to it without problems.

---

### Post by geirha on 2008-01-12
This link should address your questions: [https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

Feel free to ask more if you find anything unclear.

---

### Post by johann_p on 2008-01-12
OK, I managed to format the drive, doing this:

run "sudo gparted"
unmount the disk
delete current fat32 partition
create my new ext3 partition

Now I wanted to give the disk a new label and I did
sudo  e2label /dev/sdh usbdisk2
which showed the following error message:
"e2label: Bad magic number in super-block while trying to open /dev/sdh
Couldn't find valid filesystem superblock."

What is that supposed to mean?

And how does that relate to the "set disklabel" option in gparted?
Currently, gparted shows the disklabel type to be "msdos".

Also, for the freshly formatted disk 
  gparted shows 7.5 GiB in use
  the properties GUI for the mounted drive shows 23.5 GB in use

Why is so much storage used, and why do the two interfaces show different amounts of used data?

---

### Post by geirha on 2008-01-12
hm, could you paste the output of this command? ```
sudo fdisk -l
``` (Please put the pasted output in [code]-tags)

---

### Post by johann_p on 2008-01-12
```

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bd903

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   83  Linux

```

---

### Post by geirha on 2008-01-12
Ok, /dev/sdh is the harddrive itself, while /dev/sdh1 is the partition you've formatted, and /dev/sdh1 is the device you want to pass to e2label to change the label. 

```
df -h /media/mountpoint
``` (change /media/mountpoint to where it's actually mounted of course, alternatively you can type just "df -h" which will list all file systems). How much does that df command display as used?

Ext3's journaling uses a certain percentage of the partition to store the journaling information, so that it uses 23.5GB on a 500GB partition isn't very surprising. Not sure why gparted would display an amount so different though.

---

### Post by johann_p on 2008-01-12
Thanks that helped a lot!

I was now able to change the label and I also found 
```
tune2fs -m 0 /dev/sdh1
```
to set the reserved space to 0%

However, the discrepancy between what gparted shows and what the properties dialog shows still exists:

gparted: 7.5GiB Used, 458.26 Unused Size: 465.76

Properties: 458.3GB free, 198.0MB used.

df -h:  Size 459G Used 199M Avail: 459G


So maybe the amount "Used" reported by gparted has something to do with the necessary overhead of the file system that can never be obtained as free space for the end user?

---

