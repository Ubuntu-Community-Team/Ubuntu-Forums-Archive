---
title: "bringing an old pc back to life ..."
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by peterkeyani on 2008-04-11
Hello,

Ive just installed ubuntu 7.10 gutsy on an old NEC, pentium 4 1.5 G, 250 MB, pc that was stuffed full of spyware and viruses and was about to be thrown out. I'm posting this from the same computer so I guess it worked ok. Actually, I have to say im very impressed by how nice it looks and and the range of features even the speed despite a puny 250 MB's of RAM.

One quibble though. The pc has two disk drives each about 20 G's I think. I installed ubuntu on the first drive. System Mointer says Ive got 14.4 G available but I cant see anything about a second drive?  How do I use it?

Also, if I decide to throw a couple more MB's of RAM into the pc, how do I find out what it needs etc?

Thanks

Pete

---

### Post by hums07 on 2008-04-11
> **peterkeyani said:**
> 
One quibble though. The pc has two disk drives each about 20 G's I think. I installed ubuntu on the first drive. System Mointer says Ive got 14.4 G available but I cant see anything about a second drive?  How do I use it?

Also, if I decide to throw a couple more MB's of RAM into the pc, how do I find out what it needs etc?

Thanks

Pete
You might not include the second drive as mounted during install. You can check if the system recognizes it:```
sudo fdisk -l
```
and see if it is in the list of fstab:```
cat /etc/fstab
```please post the output of both instruction.

Simple way to upgrade RAM is by looking at the current one, pull out the memory card from the computer and see what its type is. See if there is another slot available in the computer and buy exactly the same memory type. eBay may help.

EDIT: I may have misunderstood the question. If you want to see the usage of your disk, you can use the code: ```
df
```

---

### Post by peterkeyani on 2008-04-11
> **hums07 said:**
> You might not include the second drive as mounted during install. You can check if the system recognizes it:```
sudo fdisk -l
```
and see if it is in the list of fstab:```
cat /etc/fstab
```please post the output of both instruction.

Simple way to upgrade RAM is by looking at the current one, pull out the memory card from the computer and see what its type is. See if there is another slot available in the computer and buy exactly the same memory type. eBay may help.

EDIT: I may have misunderstood the question. If you want to see the usage of your disk, you can use the code: ```
df
```

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099803

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2434      747022+   5  Extended
/dev/sda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d4c5d4c

   Device Boot      Start         End      Blocks   Id  System
pete@pete-desktop:~$

---

### Post by peterkeyani on 2008-04-11
> **hums07 said:**
> You might not include the second drive as mounted during install. You can check if the system recognizes it:```
sudo fdisk -l
```
and see if it is in the list of fstab:```
cat /etc/fstab
```please post the output of both instruction.

Simple way to upgrade RAM is by looking at the current one, pull out the memory card from the computer and see what its type is. See if there is another slot available in the computer and buy exactly the same memory type. eBay may help.

EDIT: I may have misunderstood the question. If you want to see the usage of your disk, you can use the code: ```
df
```

pete@pete-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a16ea181-52dc-4ae8-869a-4054ba2dd817 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=57b48b01-b045-c3a3-774f-0196775595cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
pete@pete-desktop:~$

---

### Post by hums07 on 2008-04-11
fdisk says your second drive has not been formatted.
If that's true, then run gparted and format it.

After that, try to mount it:
```
sudo mkdir /media/sdb
sudo mount /dev/sdb/ /media/sdb
```

You may now see the drive in the monitor, or you may need to restart.
If you want to make it automount every time you start Ubuntu, then you need to edit /etc/fstab.

---

### Post by peterkeyani on 2008-04-11
> **hums07 said:**
> fdisk says your second drive has not been formatted.
If that's true, then run gparted and format it.

After that, try to mount it:
```
sudo mkdir /media/sdb
sudo mount /dev/sdb/ /media/sdb
```

You may now see the drive in the monitor, or you may need to restart.
If you want to make it automount every time you start Ubuntu, then you need to edit /etc/fstab.

Thanks

How  I do that, please? Which of the terms is my 2nd drive for instance?

---

### Post by hums07 on 2008-04-11
To edit your fstab, run this code
```
gksudo gedit /etc/fstab
```
It will ask for password and open an editor.

Add this lines:
> #/dev/sdb  #this line is just a comment actually
/dev/sdb  /media/sdb ext3 defaults 0 2
[COLOR="Blue"][B]NOTE: I assume you format the second drive with ext3 format.
[/B][/COLOR]
So your fstab should look like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=a16ea181-52dc-4ae8-869a-4054ba2dd817 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=57b48b01-b045-c3a3-774f-0196775595cf none swap sw 0 0
#/dev/sdb  
/dev/sdb  /media/sdb ext3 defaults 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

Save the file and close the editor.

If you wish to know more about fstab, it's here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

