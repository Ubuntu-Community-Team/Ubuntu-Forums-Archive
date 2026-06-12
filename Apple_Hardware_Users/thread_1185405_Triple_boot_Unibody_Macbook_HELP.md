---
title: "Triple boot Unibody Macbook HELP?"
date: 2009-06-12
forum: Apple Hardware Users
---

### Post by cephus6 on 2009-06-12
I am making the swithc to a 13" macbook.

I have been a long time windows user and presently have a VISTA/UBUNTU dual boot.

I would like to have a triple boot system and I have read several guides and believe it is possible.

I would like to setup my 320GB hard drive with the following partitions:

OSX       80GB
VISTA     80GB
UBUNTU    40GB
DATA     120GB

However from my reading I am not sure this is possible with the 5 partitions.

Can you recommend a good guide to follow to setup and can I have recommendations on 5 partitions.

Thanks in advance
Robert

---

### Post by hraposo on 2009-06-12
my english is not good but I'v triple boot without problems.
First, with live cd of ubuntu, use gparted, create 4 partitions,first for mac, second for windows and 3 for Linux root and 5 for swap.
Boot from mac os x, and with disk utilities erase mac partition (format).Install Mac OS X, then Windows and Linux at end. Wen you answer of questions of linux select advanced proprities and selecte de grub instalation grub in begin of linux partition.
BUT FIRST OF THIS ALL INSTALL reFIt, (AN BOOT MANAGER) IN MAC.

---

### Post by cephus6 on 2009-06-12
Ok, So if I follow I am limited to 4 partitions.

In that case what if I use resize the partition

to:

OSX 80GB
VISTA 120GB
DATA 120GB

Then I use WUBI to install Ubuntu under windows?

Would that work are there any issues using WUBI?

---

### Post by cyberdork33 on 2009-06-12
Yes it will be tough to do what you are considering.

First, there is an EFI partition at the beginning of the disk, and that has to be there. The Apple Firmware (unless it has changed) is only capable of booting a "legacy OS" from the first four partitions because of their method of emulating the older-style MBR partition table. 

Additionally, Windows is in capable of reading any partitions greater then 4 because of the same issue (it can only see the MBR partition table). Because of that, you have to have your storage partition in the first four to allow windows to use it. Once Linux is booted, it is capable of using the normal GUID Partition Table (GPT) to function, and thus, only the bootable partition needs to be in the first 4.

Now, OS X actually doesn't have to be in the first 4 partitions at all! It is actually happy booting from the 20th partition (if you have one).

So my suggestion would be something like:

1. EFI
2. Windows
3. Ubuntu - /
4. Storage
5. OS X
6. Ubuntu swap

you can install Ubuntu with WUBI, but there may be other issues. It has been done before on a Mac though.

---

### Post by cephus6 on 2009-06-19
I just wanted to give an update.  I have my new macbook up and running.  I ended up using bootcamp and wubi to install vista and jaunty.

Everything is running smooth and I cannot tell a performance hit, but I have not done any performance intensive task yet.

Still trying to sort thru the jaunty issues of getting sound and trackpad and the like.

---

