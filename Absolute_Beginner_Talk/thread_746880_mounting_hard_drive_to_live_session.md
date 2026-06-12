---
title: "mounting hard drive to live session"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by SurlyDune on 2008-04-06
i need to copy some files from a live session but i dont know how to mount my hd to the live session can anyone help?

---

### Post by zeronothing on 2008-04-06
so your using a live cd on a machine, and you need to mount a hard drive that is on the system. does the system have a ntfs hard drive or a linux partitioned hard drive?

---

### Post by artfwo on 2008-04-06
Is your HDD visible in the Places -> Computer? If yes, then you only have to double-click it's icon and it will be auto-mounted.

If not, then you'll have to manually find the associated device for the required partition (e.g. first partition on first hard disk will be /dev/sda1), then run the following commands in the Terminal:

```
ubuntu@ubuntu:~$ mkdir mydisk
ubuntu@ubuntu:~$ sudo mount -o umask=777 /dev/sda1 mydisk
```

And check the folder "mydisk" in your home directory. When done, make sure to unmount the folder:

```
ubuntu@ubuntu:~$ sudo umount mydisk
```

Hope this helps :)

---

### Post by SurlyDune on 2008-04-06
ntsf was the original partition but i used the slider bar when installing ubuntu to partition the hd for it.
i just tried to go into the places>computer and right click on the partition and select mount volume and i got the error message

> Cannot mount volume
unable to mount volume

details
mount: wrong fs type, bad option, bad superlock on /
dev/sda2,     missing codepage or helper program,
or other error     In some cases useful info is found
in syslog - try    dmesg | tail or so

dont know what to do or where syslog even is

---

### Post by SurlyDune on 2008-04-06
@ artfwo my drive shows up in place>computer and i try to double click it and i get the same error as above

---

### Post by zeronothing on 2008-04-06
you will need to if you already haven't done it, is install the ntfs module to mount the partition. you will need to open up synaptic and install these two things. 

go to system->administration->synaptic

click search and in the text box put ntfs-3g

then just click on the checkbox to install it

also do another in synaptic to install ntfs-config

install those to things in order to mount the partition

---

### Post by zeronothing on 2008-04-06
also for some more information on your disks do this command so we can get a better look of the partition setup. execute this command and paste in a new post here what you get in terminal. open up terminal and execute this:

sudo fdisk -l

---

### Post by SurlyDune on 2008-04-06
tried installing both ntfs-config and ntfs-3g and i got  a similar error message when i ran the sudo command i got this
> 
Unable to open -

Unable to open -

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17f817f7

   Device Boot      Start         End      Blocks         Id  System
/dev/sda1   *           1       17064   137066548+   7  HPFS/NTFS
/dev/sda2           17065       24019   55866037+  83  Linux
/dev/sda3           24020       24321     2425815    5  Extended
/dev/sda5           24020       24321     2425783+  82  Linux swap / Solaris


---

### Post by SurlyDune on 2008-04-06
something kinda weird, i can mount my windows partition but not my ubuntu one

---

