---
title: "How large to make the Partition"
date: 2007-06-18
forum: Apple Intel Users
---

### Post by speedemonV12 on 2007-06-18
hey guys, i jsut got my external hd, from seagate, so i can backup my os x drive, and then wipe the drive clean, and triple boot with Ubuntu! Im going to be using os x, window, and ubuntu. But I was wondering how large i should make the ubuntu partiton, since I have not used linux much before, i cant remember how large the OS is. I dont plan on saving a lot of files on the ubuntu partition. Ill be keeping them on the external hd. So anyways, was wondering what size i should make the partition? what would be reasonable

---

### Post by yabbadabbadont on 2007-06-18
If you aren't going to be storing a lot of data on the partition, just the OS, then 6 or 8 gigabytes should be enough.

---

### Post by ronocdh on 2007-06-19
> **yabbadabbadont said:**
> If you aren't going to be storing a lot of data on the partition, just the OS, then 6 or 8 gigabytes should be enough.
I second this. It's possible to set up filesharing between partitions (I recommend you format your Windows installation as FAT32), and this greatly reduces the space needed for Linux, and also lets you wipe the installation at the drop of a hat, in case anything goes wrong (because your data is stored elsewhere).

---

### Post by speedemonV12 on 2007-06-19
So 6 to 8 gig will allow for most of the common apps, and a few others, and then all the visual effects as well? I also plan to set it up so that i can access my OS X partition from within linux. I dont use my windows partition for anything except gaming. It is currently set at 20 gb, I play CS Source on it. So i store all my files on the os x partition, and ext hd. I hope it is possible to be in linux, and using something like amarok to play my music that I have stored on my os x partition. 

ronocdh - did you mean that since i wont be storing files, that the linux would not have to be large, or the fact that windows is fat32?  (My windows is currently FAT32)


edit: You know how bootcamp allows you to restore your disk to one entire partition, therefore deleting the windows partition. Is it possible to use some other program to wipe out the linux partition, and merge it with the os x one again, so i would then have only os x and windows? I dont plan on deleting linux, but just in case i want to get rid of it, I dont really want to have to redo the entire drive, but i can if need be.

---

### Post by cevans on 2007-06-19
6 to 8 GiB will allow for a large number of applications; if I recall correctly, I've installed all of the default software from Ubuntu, Kubuntu, and Xubuntu in less than 8 GiB. I've never needed more than 10 to 15 GiB for my root partition (I keep my data on separate partitions). OS X applications tend to be surprisingly bloated in size by comparison.

---

### Post by yabbadabbadont on 2007-06-19
I've been using 12GiB for my root partition for several different linux distributions.  Because I have /home on its own partition, I've never come close to running out of space on root.  Your experience should be similar since you are going to store your data on a different partition from root.

Edit: The most I've ever filled up root was to somewhere between 4 and 6 gigabytes used, which is why I originally recommended 6 to 8.  I'm using a custom minimal installation currently and am only using 1.6 GiB out of the 12 I have allocated.  :D

---

### Post by ivesjd on 2007-06-20
Boot camp will not function unless you have two partitions like what it set-up in the begining. If you want to remove Ubuntu, you can do it from the terminal. Or you can use iPartition. If you want to get rid of the Ubuntu partition and merge the space with your windows part, you can use gparted on the ubuntu live cd.

---

