---
title: "Ntfs"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by axlgothika on 2007-04-18
Hello everyone, I want to install ubuntu tomorow, but I have a partition that has the NTFS File System and I don't want to lose it... as far as I've read, Ubuntu only reads NTFS and does not write in NTFS.... I understand there is a convertion NTFS-X3 or something which enables read&write. Can I change the File System without formatiing and should I ever decide to return to Windows, can I convert it back to NTFS without losing my data on the partition.... 

If i currently have Windows installed, wil the settings in windows remain in Ubuntu too? For example, I use the ePower Management utility (which I know hasn't a version in Linux) and I've turned my CPU to "medium" instead of "maximum"... will I be able to change my CPU freq to save battery on my lappy?

Thanks and excuse my English, it is not so good

---

### Post by cookiefreak on 2007-04-18
i have the same question about the NTFS...

---

### Post by Stickymaddness on 2007-04-18
Hi axlgothika,

Welcome to The Ubuntu Forums, and to Ubuntu!! 

Ubuntu uses the ntfs-3g driver to read & write to ntfs partitions, you can read more about it [here]("http://ubuntuforums.org/showthread.php?t=217009"). 

You can install Ubuntu without formatting, but you will need to make new partitions for Ubuntu which can be done from the Ubuntu install Disk, either manually or automatically. 

**Please note you cannot install Ubuntu onto an NTFS partition!**

I'm not familiar with "ePower Management" but I'm sure you will find a suitable Ubuntu replacement for this application.

Good Luck and enjoy!

---

### Post by BarfBag on 2007-04-18
First of all, your English is great.  Trust me, I've had to help people TERRIBLE English before.

I don't think there's a way of non-destructively changing your NTFS partition.  From what I've heard, NTFS-3G is safe enough to use.  I'm not 100% positive, though.  [Here are instructions on how to install it.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

Settings of that nature will not stick.  However, you can easily change your CPU frequency in Ubuntu.

---

### Post by joeblow1102 on 2007-04-18
You can leave your ntfs partition as ntfs.  The driver is called ntfs-3g and there are multiple threads dedicated to getting this work for you.

---

### Post by Michaelt74 on 2007-04-18
First, mount windows (the hda1 icon) on your desktop

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

Next, download ntfs-config

[http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

Follow the instructions and you should be able to write to the ntfs partition.

---

### Post by surfin.stitch on 2007-04-18
first of all, as ubuntu cannot be installed on an ntfs partition, you have to resize your ntfs partition and allocate space for your ubuntu installation. you can do this during installation.. just choose resize windows/ntfs partition (im not sure, i forgot) :)

then install ubuntu on the newly freed space..

then to have read and write access to your ntfs/windows partition.. just install ntfs-config with the following command..

sudo apt-get install ntfs-config

then you should be good to go.. :)
for more, check this site.. [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

i also recommend installing from the live cd so that everything will be graphical and easier.. :)

---

### Post by cypherzero on 2007-04-18
I did this fine, the installer is really user-friendly, if somewhat buggy. You can resize your partitions no problem, just remember to create two new partitions for Linux - one for the install (big enough for your Linux data) and one for the swap file (3x your RAM)

---

