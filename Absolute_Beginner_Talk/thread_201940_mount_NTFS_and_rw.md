---
title: "mount NTFS and rw"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-22
How can I mount some NTFS partition on ubuntu. I've installed captive but when i try to mount it says about fusemount and when i tried to install that fuse program it crashed saying that my c compiler can't make executables. pls help

---

### Post by underdog on 2006-06-22
Not sure about your fusemount problem, but If you are having problems compiling, i suggest

sudo apt-get install build-essential

---

### Post by FuzZy2006 on 2006-06-22
do you know any other easier possibility to mount ntfs partitions for read/write?

---

### Post by dronepower on 2006-06-22
[QUOTE=FuzZy2006]do you know any other easier possibility to mount ntfs partitions for read/write?[/QUOTE]

you mean like this?   I got this from the dapper manual



 How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only

    * Read #General Notes
    * Read #How to list partition tables 


    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

    * To mount Windows partition 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

    * To unmount Windows partition 

sudo umount /media/windows/


to have it set on bootup:


 How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

---

### Post by Kilz on 2006-06-22
[QUOTE=FuzZy2006]do you know any other easier possibility to mount ntfs partitions for read/write?[/QUOTE]
I don't think writing to a ntfs partition is possible, at least not safely. I recommend setting up a small fat32 partition and mounting it. Both Linux and windows will be able to read and write to it so you can share files between the two..

---

### Post by Apple 101 on 2006-06-22
You could leave the Ubuntu files on its partition, boot back into Windows, and access your Linux ext2/3 drives from there.  That's what I do with NTFS writing problems.  I have a link for loading the ext2/3 drives from Windows (when I can find it).

---

