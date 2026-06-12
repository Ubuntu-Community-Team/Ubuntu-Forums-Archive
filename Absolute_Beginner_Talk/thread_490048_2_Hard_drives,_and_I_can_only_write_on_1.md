---
title: "2 Hard drives, and I can only write on 1"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by galapagos on 2007-07-02
I have a 20 gig hard drive running Ubantu and another 80 gig hard drive (actual separate drives) running windows.  While I dont want to get rid of windows (yet),  I would like to be able to put files/folders on the 80gig hard drive while on linux.  I have no trouble accessing files on the 80 gig, but changing or adding files doesn't work.    The 80gig is NTFS while the 20 is FAT32.  

let me know if you need more information, and thanks in advance.  



betty swollocks

---

### Post by paradoc on 2007-07-02
Defrag your 80GB HD first, 
Use a GParted CD or a Ubuntu LiveCD to create a partition within windows, of a size suitable to your requirements, and make sure it is formatted to **FAT32 **(you can write  and access NTfs  from Linux but you can't change anything).  
Post further for assistance if you get stuck, there's loads of help for you here!

---

### Post by eternalsword on 2007-07-02
shouldn't need to create any new partitions.  ntfs-3g will allow writing to ntfs.  see [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html) for a guide

where it says
sudo apt-get install ntfs-config

that should be run from the terminal
to open the terminal hit alt+f2 and type in gnome-terminal in the run dialog or it might be in your Applications menu (it's been too long since I've used a fresh install to remember :p )

---

