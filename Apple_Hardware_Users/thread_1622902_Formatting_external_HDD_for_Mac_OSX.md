---
title: "Formatting external HDD for Mac OSX"
date: 2010-11-16
forum: Apple Hardware Users
---

### Post by potatan on 2010-11-16
Hi,

I have used a live CD to recover a friend's old photographs from a long-broken Windows machine.  She would like the data back in an external HDD enclosure which she will then connect to her MacBook and use as backup / extended storage.

My question - is it possible to format this drive (using Ubuntu) as a Mac-type partition?  I don't have access to a Mac so I am hoping that Gparted or something similar may be able to help.  I'm also unfamiliar with Macs generally.

Alternatively, could I format it with NTFS, i.e. will that be okay for Mac?  

Note that she is not a power user or video editor etc., so no need for a very elegant solution.  I just want to pop round, give her the drive with the data on it, and have it accessible straight away from her Mac via USB.

It's a 160GB SATA 3.5" drive.

Many thanks

---

### Post by ajgreeny on 2010-11-16
Fat32 is OK for mac read/write, but ntfs can be a problem without added utilities.

I do not use mac so have no idea how good those are, but have a look at this google search page for lots more details.
[http://www.google.co.uk/search?q=can+mac+read+ntfs&ie=UTF-8](http://www.google.co.uk/search?q=can+mac+read+ntfs&ie=UTF-8)

---

### Post by linux-hack on 2010-11-16
If you want to read ntfs on mac thats ok .. but if you want to write you need third party software... And I don't think you can format it with linux to be a proper MAC OSX parition..

It needs to be a hfs (I think thats write) type partition journalized.

[http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)
[http://www.macupdate.com/info.php/id/26288/ntfs-for-mac-os-x](http://www.macupdate.com/info.php/id/26288/ntfs-for-mac-os-x)

---

### Post by entangled on 2010-11-16
I am an iMac user and I can confirm that my one TB external drive, formatted with FAT32 as one partition, can be used for read and write under Mac OSX 10.6.5.

---

### Post by potatan on 2010-11-19
Thanks all.  Went with FAT32 in the end.

There is soemthing about a 4GB file size restriction, but she's no power user so I'm guessing this will not be a problem for her.

Solved, cheers.

---

