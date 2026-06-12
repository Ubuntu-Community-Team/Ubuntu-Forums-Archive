---
title: "Hola from India"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by redenex on 2007-03-04
Just scrapped Windows XP crap from my computer and installed UBUNTU 6.06. Just saying HI. Updated files are still being downloaded, but I believe I may need some help to transfer files from the XP folders to Linux partition. I copied all the files from my XP folders to another hard disk, and formatted and installed Linux on this computer. Now, I need to connect the back up HDD and copy back the files onto Linux HDD. I hope I made myself clear, if not, I shall check in back later! :guitar: :lolflag: 

Have a great Sunday everyone and rock on!

---

### Post by equal on 2007-03-04
is the other drive a USB drive or is it a standard drive? Do you know what filesystem the other disc is formatted to?

---

### Post by sriram on 2007-03-04
u have to edit the fstab file and mount them according to the partition type ..
create directories in /media folder based on the no of partitions

---

### Post by redenex on 2007-03-04
:guitar: 

Phew! My computer is on a highway! Never felt such a fast performance on my system before!


Anyways, The "other" HDD onto which I have dumped all my data is NTFS and it is a regular HDD (Not USB). I believe I am unable to mount it as a volume, though Linux is detecting the HDD. I am afraid I may need to cut a CD of all the data I have and then copy it to Linux volume - unless someone here has an alternative that is!

:KS

---

### Post by redenex on 2007-03-04
And...... this is the fist time in my entire life I am working on Linux. All I have is the "little" knowledge of UNIX, which I worked on way back in 1993-1996.

Ironically, I am not even able to get to the command prompt on Linux, but I believe I can find a way soon! :popcorn:

---

### Post by jvc26 on 2007-03-04
Applications -> Accessories -> Terminal
Il

---

### Post by xmastree on 2007-03-04
assuming you can install the disk as a primary slave, you will be able to get at the data on it.

See [this](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows) for information about how to mount the partition. In that example, they use hda1 but yours will be **hdb1** if it's primary slave.

---

### Post by redenex on 2007-03-04
Thank you, I shall check it out and post what I come across! Cheers!

---

### Post by redenex on 2007-03-04
Well, I have basically connected the backup HDD to the CD Rom cable. The promary HDD on this computer has been formatted and Linux is installed with a single partition. All the backup is on the "attached" HDD, so is there a way to mount it?

---

### Post by xmastree on 2007-03-04
Is it jumpered as master or slave? If it's master, it will be **hdc** if it's slave, it's **hdd**. So, make a mount point for it:

sudo mkdir /media/windows

and mount it like this:
sudo mount /dev/**hdc1** /media/windows/ -t ntfs -o nls=utf8,umask=0222
or
sudo mount /dev/**hdd1** /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

### Post by redenex on 2007-03-04
Thanks a lot for ll the help! I al so found another thread in the forum and it helped! I got to mount the volume and currently copying all my backdata to Linux volume!

Thanks a bunch, and I hope someday I can help with some one  else too! :popcorn:

---

