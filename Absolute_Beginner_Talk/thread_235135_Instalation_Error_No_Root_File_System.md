---
title: "Instalation Error: No Root File System"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by murrius on 2006-08-12
I am totally new to Linux and totally exited about saying goodbye to Windows. 

To prepare for the installation, I created three new partitions on a new hard drive: 8 GB EXT 3 parimary partition for Linux, a 1 GB Linux swap partition, and a 20 GB FAT32 partition for shared Linux / Windows files. I also have XP installed on this hard drive on it's own partition and I intend to dual boot. 

I downloaded the Ubuntu instalation file for Dapper Drake and burned it to a DVD. I re-booted and started the install process. Everything goes great until the partition process. I select manual partition and my swap and EXT3 ( / ) partition show up fine. I select those but when the program tries to start the instalation process I get "Error, No Root File System" and it will not proceed, even though I believe I have created a root file system.  I've gone through this a number of times with the same result. I've searched the support threads but I do not think I know enough about Linux to know whether some of the threads apply to the problem I am having or not. I'm hoping someone can point me in the right direction.

Thanks,

Randall

---

### Post by Pawka on 2006-08-12
You can simply let installer to create partitions manualy. Just delete your ext3 and swap partitions and run installation again. When you'll be asked about partitions, choise "use free space" (or something like this).

---

### Post by murrius on 2006-08-12
Ok, thanks, I will try that.

Randall

---

### Post by murrius on 2006-08-13
As it turned out, there was a partition error on the disk. I re-formated the disk and then created a partition for XP and two other partitions for media etc. I left a lot of unallocated mbs. Then I installed Ubuntu without a hitch using the options you had suggested. Thanks.

---

