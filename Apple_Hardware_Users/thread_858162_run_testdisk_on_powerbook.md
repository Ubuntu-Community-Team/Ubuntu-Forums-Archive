---
title: "run testdisk on powerbook"
date: 2008-07-13
forum: Apple Hardware Users
---

### Post by Brammm on 2008-07-13
Hey all,

My powerbook's HD crashed a while ago but I'd like to try and salvage the data from it, seeing as I didn't have any recent backups.

Now I've done this before on a windows pc, but now I'd like to try it on a linux pc. I got xubuntu 6.06 and ubuntu 5.10, 6.06 and I put testdisk for linux on my usb stick. I can put the folder on my desktop, I can access it, I see the "testdisk_static" executable, but when I double click it, nothing happens...

Am I doing anything wrong?

---

### Post by DonnieP on 2008-07-13
> **Brammm said:**
> Now I've done this before on a windows pc, but now I'd like to try it on a linux pc. I got xubuntu 6.06 and ubuntu 5.10, 6.06 and I put testdisk for linux on my usb stick. I can put the folder on my desktop, I can access it, I see the "testdisk_static" executable, but when I double click it, nothing happens...
Did you follow these directions for Linux from the TestDisk site?
>   Precompiled binaries

The following instructions download the archive and run TestDisk or PhotoRec.

wget [http://www.cgsecurity.org/testdisk-6.7.linuxstatic.tar.bz2](http://www.cgsecurity.org/testdisk-6.7.linuxstatic.tar.bz2)
tar xjf testdisk-6.7.linuxstatic.tar.bz2
cd testdisk-6.7/linux

TestDisk and PhotoRec must be run as root:

    * Using sudo: sudo ./testdisk_static, sudo ./photorec_static
    * Using su: su -c ./testdisk_static, su -c ./photorec_static 

---

### Post by Brammm on 2008-07-13
God, I must've missed those. Thanks, I feel kinda stupid :p

---

### Post by Brammm on 2008-07-13
great, now it says "cannot execute binary file"

---

### Post by DonnieP on 2008-07-13
> **Brammm said:**
> great, now it says "cannot execute binary file"
I notice now that TestDisk is in the repo's (even though the TestDisk homepage didn't mention debs).  Anyway, synaptic will be the way to go here.  You should be able to delete the files you've already downloaded.

---

