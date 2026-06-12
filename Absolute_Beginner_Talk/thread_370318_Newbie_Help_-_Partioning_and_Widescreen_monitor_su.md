---
title: "Newbie Help - Partioning and Widescreen monitor support"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by SomeoneSomewhere on 2007-02-25
Hi,

I have tried to install Ubuntu and scare myself.

I have a new Acer computer that has a 160gb hd partitioned 80gb NTFC and 80gb FAT32. I want to install a dual boot but don't know how to partition a section for Ubuntu... what do people suggest is best.

I also noticed that when I got to the install screen, it did not support my widescreen monitor!!! Any ideas?

Thanks a million
Matt

---

### Post by george29 on 2007-02-25
Can't help you with the monitor - but if you search the forums and do a google search for Xorg configuration and your monitor you may find some information (post up what info you have on the monitor - resolution, manufacturer etc) someone maybe able to help you.

with the partitioning - i presume you have windows installed to the NTFS partition and use the FAT32 partition for data storage? 

if this is the case you need to back up all your data, defragment the partition and then resize it to leave 10-20gigs of free space in a new extended partition (not a primary - as you will need to create a swap partition. etc). the Ubuntu installer can then automagically use this free space to install into - creating all the necessary swap partitions etc

there are plenty of threads on the forum and probably how to documents on the web if you google for 'installing ubuntu' and 'ubuntu guide' which will have the information you need - have a read, digest, then if you have any questions come back and someone will happily answer your questions and help you to get a great OS installed on your PC.

---

### Post by SomeoneSomewhere on 2007-02-25
If I copied all the data to the NTFC partition and just formatted the FAT for Ubuntu, would this work and would it be a good solution. Could I still access the data on both operating systems?

---

### Post by antoz on 2007-02-25
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Check out this link it is very helpfull, just slect partitioning fro the menu on the left.

cheers, A

---

### Post by george29 on 2007-02-25
If you copied all the data to the NTFS partition. you could then use reformat the FAT partition as Ext3 which is the default filesystem for Ubuntu.. 

i would then install a driver in windows that allows you to read and write to the Ext3 partition..
[http://www.fs-driver.org/](http://www.fs-driver.org/)

and then install the ntfs-3g driver in ubuntu (bit more involved) which will allow you to read and write to the windows partition - be aware that this driver has only just left or may still be beta software - so it could work perfectly for you or you could end up screwing some data up on the ntfs partition.. 

i find the most elegant (lazy and requires the least faffing and hassle) way (i use this method) is to have a NTFS partition for windows, an Ext3 partition for ubuntu and a FAT32 partition which i use to store shared files, data etc as both OS's will read FAT32 without a problem.

up to you which way you choose to go.

george

---

