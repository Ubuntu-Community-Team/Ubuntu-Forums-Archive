---
title: "Purchasing a new HDD"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Disparition on 2008-02-02
Read some of the posts about the issues on external HDDs. And decided to buy a "normal" hard disk. As far as I see, Ubuntu in my computer uses something called ext3 as file system. The standard ones are  NTFS I suppose. How am I going to format it to ext3 ?

---

### Post by Aurora@FleetBuzz on 2008-02-02
If you install Ubuntu to the new HDD, it will format automatically.  You can also do manually during the set up.  I set mine up for EXT3 for my root and home, a swap partition, and the remainder of the HDD to FAT32 (before I learned that Gutsy will read and write NFTS!).  I would "rehearse" the install via a live CD before the actual doing....

---

### Post by insane_alien on 2008-02-02
if your are setting this up to be an additional drive then when it has been physically installed go to synaptic and install 'gparted'. or, if you don't mind a bit of command line
```
sudo aptitude install gparted
``` will sort you out.

once it is installed fire it up and select your new drive from the menu in the top right. it'll be /dev/sdb or something. then click new partition. this will ask you to write a new disk label or something, just select the default then you'll be asked for details about the partition you want to make such as size and filesystem. select ext3 if you just want to play it safe or ntfs if you want to share with a windows install. once thats done you might need to edit /etc/fstab to get it to mount in a desired place every boot time.

---

### Post by laidback on 2008-02-02
For my money use Gparted.

---

### Post by Aurora@FleetBuzz on 2008-02-02
Here's a link to some videos that may help.
[http://www.linux.com/articles/114157](http://www.linux.com/articles/114157)

---

### Post by bumanie on 2008-02-02
The above posts are correct in what they are saying, but I wonder what you mean by a 'normal' hard drive. Also what you do to re formatting and whether you need to edit /etc/fstab will depend on how you propose to use it. Whether it is a permanent external drive, a storage device or backup device can determine what you may or may not need to do to. I use mine for carrying around certain files from computer to computer and as ubuntu can read/write ntfs and fat 32 as can windows, I have it equally divided into ntfs and fat 32 and can use it on any ubuntu and any windows computer (even win 95/8). If I was using it exclusively on linux I would format it to ext3. So what file system/s you use depends on how you propose to use the drive.

---

