---
title: "Grub error 22 after erasing WinXP partition"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-10-09
Until yesterday, I was dual booting 6.06 and WinXP, each with it's own partition on one drive.  Then I wiped the XP partition entirely (currently unallocated space), and I now receive Grub error 22 (partition not found) when booting.

I thought I had set up Grub from scratch when I did this from a Grub prompt, after I had erased the XP partition:
find /grub/boot/stage1 - reported (hd1,1)
root (hd1,1) - reported ok
setup (hd1,1) - reported ok

But when I boot, I still get the error 22.  My problem is that I don't know how to fix it when working from the live cd.  How do I get into the menu.lst (isn't that what I need to check?) from the live cd, or at bootup after I get the error message?

Thanks

---

### Post by bulldog on 2006-10-09
To get to your menu.lst you have to mount your Ubuntu partition.

Boot up the live cd and make a mountpoint```
sudo mkdir /mnt/ubuntu
```

Now you have to mount your partition```
sudo mount /dev/??? /mnt/ubuntu
```

Where ??? stands for your ubuntu partition.

Keep in mind now you removed one? partition,the counting will be different as before!!

Error 22 means:22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

If the mounting was succesfull to get to your menu.lst```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

If Ubuntu was on your third partition example hd0,3,now you removed one partition it will be hd0,2.

You could make a new partition in the unallocated space,then is everything as it was.

---

### Post by uzd4ce on 2006-10-09
Cool thanks, I think that's exactly what I needed to know.  I'm going to try formatting that unallocated space as something and see if that fixes it.

If not, now I know how to go in and make the changes I need.

Thanks

---

