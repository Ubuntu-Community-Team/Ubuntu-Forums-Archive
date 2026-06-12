---
title: "Gparted Question-  how do I format?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by ben0r on 2007-04-28
I think all this did was create a partition table.

what do i do now to format the drive? and/or get it mounted so i dont have to mount it every time i boot up?

[IMG]http://www.patsargent.com/gparted.png[/IMG]

---

### Post by Nythain on 2007-04-28
try clicking on the unallocated space part and see if the "new" option opens up... if so, click it and create a partition on it... format in whatever filesystem you want... if it doesnt open up the "new" option, and there's no data to lose on the hard drive, click on the already created partition there, select "delete", then "new" should open up... i havent used gparted in a long time so im not the most refreshed at setting up partitions with it

---

### Post by ben0r on 2007-04-28
nice, i'm almost embarrassed


how might I add the drive so it mounts everytime i startup?

---

### Post by Nythain on 2007-04-28
first you have to create a place for it to mount... like say /data
```

sudo mkdir /data

```
then, depending on what filesystem you created it with you have to add a line to your /etc/fstab, something like this
```

/dev/sdb1    /data    ext3   defaults   0     2

```
granted some of that will change, like where you want it mounted, and the filesystem you formatted it in, then any necessary options other than defaults, that line was directly taken from my fstab so dont just copy and paste it...
save the fstab, then try rebooting and see if it automounted

---

### Post by sailor2001 on 2007-04-28
on the boot screen, count down all that's listed starting with the #o (most likely ubuntu latest kernal). remember the #..... In the terminal then    sudo gedit /boot/grub/menu.lst  and change the default start-up to the # you wanted

---

### Post by thefoolisme on 2007-04-28
IF you click on "Unallocated", the "new" Icon will be available.  Select new, and the format type, ext, FAT32, NTFS, etc. and it will create and format the partition.

---

