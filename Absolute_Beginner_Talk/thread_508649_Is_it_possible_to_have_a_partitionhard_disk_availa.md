---
title: "Is it possible to have a partition/hard disk available to both WinXP and Ubuntu?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Sir Funk on 2007-07-24
Hey everyone,

What I'd like to do is to create a partition on my main Hard disk that I intend to store data such as music and movies so that I could listen/view them whether I'm booting into WinXP or Ubuntu.  Is this possible to do?  I'd rather not have two sets of my mp3s/dvds, but i'm not sure how to make this work.

Thanks!

-Funk

---

### Post by Rocket2DMn on 2007-07-24
Absolutely!  Create the partition - you can use ext3 file system if you make it from Ubuntu, or NTFS is you make it from Windows.  I use ntfs, but I would suggest ext3 b/c nobody really likes dealing with ntfs in Ubuntu.
You can get a simple driver for Windows to read ext2/3 drives - [www.fs-driver.org](www.fs-driver.org)
Enjoy

Oh, and you will use gparted to create the partition (if you use Ubuntu to do it).  I've never used it myself, but people find it easy enough as long as you have the disk space available.

---

### Post by LaRoza on 2007-07-24
Yes, you can make a partition for both. If the files you intend to store on this partition are under 4 GB, I recommend a FAT32 partition.

You can resize your partitions, and make a new one with GParted. I recommend using the LiveCD. You can get it from the link in my sig.

---

### Post by Orochi on 2007-07-24
Both Ubuntu and Windows can read and write to FAT32 natively. There is a driver (posted above) that lets Windows XP read and write to ext3 drives (Ubuntu's default format). To get Ubuntu to write to NTFS drives you have to instead ntfs-3g from the repositories, but it's not exactly perfect and can cause data corruption. I suggest you use FAT32 or ext3. If you have free space on your drive you can use gparted to make the partition.

It's actually probably easiest to just put all your music on the Ubuntu partition and then install the driver in XP that allows Windows to read ext3 drives.

---

### Post by rickycodie on 2007-07-24
if you want to use ntfs automatix can mount it for you.

---

### Post by Sir Funk on 2007-07-24
Thanks for all your help, I really appreciate it! :)

-Funk

---

### Post by bodhi.zazen on 2007-07-24
> **rickycodie said:**
> if you want to use ntfs automatix can mount it for you.

Err ... Automatix does not mount hard drives ..

You can mount ntfs with the default Ubuntu installation. If you want read-write access you need to install ntfs-3g. If you want a gui, install ntfs-config 

You should install all this with apt-get, aptitude, syanptic, or add/remove programs (the last two are gui tools). 

All this is available in Ubuntu, all with a few clicks. Automatic is not needed.

---

### Post by BlueNoteExpress on 2007-07-24
How well does the ext3 driver for Windows work?  I might try that at home.

---

### Post by Rocket2DMn on 2007-07-24
Works fine for me, but I rarely use Windows.  I haven't heard complaints about it, though.

---

### Post by Orochi on 2007-07-24
It works perfectly for me. The only thing they say is don't use it to mount an ext3 partition on Windows, then hibernate and use GRUB to boot into Linux as it may cause errors.

---

### Post by Epilonsama on 2007-07-25
Im not a fan of fs-driver cuz it mounts ur ext3 hd as an ext2 hd, im sure this can also create data corruption.

---

### Post by Orochi on 2007-07-26
> **Epilonsama said:**
> Im not a fan of fs-driver cuz it mounts ur ext3 hd as an ext2 hd, im sure this can also create data corruption.
No, ext3 is designed to be able to mount as ext2 in order to be backwards compatible with older systems that can't read ext3. It's not going to cause corruption.

---

### Post by LaRoza on 2007-07-26
But doesn't this driver allow the user to alter ANY file? That is dangerous.

---

### Post by styphon on 2007-07-26
> **LaRoza said:**
> But doesn't this driver allow the user to alter ANY file? That is dangerous.

Surely its not dangerous if all you intend on using it for is storing mp3's and images and the likes? As long as you know which partition to use there shouldn't be any problems.

---

### Post by Orochi on 2007-07-26
> **LaRoza said:**
> But doesn't this driver allow the user to alter ANY file? That is dangerous.

Yes, it can be a security risk because it ignores ext3 ownership and permissions. So if someone gained access to your Windows partition they could edit or view any file they wanted on your ext3 partition.

---

