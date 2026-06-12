---
title: "how to resize my /home partition!!!"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2008-04-20
hello everyone i want to resize my hard drive . cos initially when i got my system it has 160gb and i partition it to ;

37gb /root
78gb /home
37gb fat32

now i want to add the fat32 to my home partition please how do i go about it without loosin my documents

thanks

---

### Post by nofrendo on 2008-04-20
Put in your liveCD and do it in Gparted. Delete the fat32 partition and expand the /home partition. Backing up data is reccommended

---

### Post by Oldsoldier2003 on 2008-04-20
> **nnamdi said:**
> hello everyone i want to resize my hard drive . cos initially when i got my system it has 160gb and i partition it to ;

37gb /root
78gb /home
37gb fat32

now i want to add the fat32 to my home partition please how do i go about it without loosin my documents

thanks

what you need to do is download a [GParted Live CD]("http://gparted-livecd.tuxfamily.org/")  and resize your partitions. However, when you "grow" your home, the space you use needs to be in an adjacent partition. please post the output of 

```
sudo fdisk -l
```

---

### Post by Can+~ on 2008-04-20
The 90s called, they want their file system back. :lolflag:

As everyone has suggested, use gparted,and expand the current one, but I suggest backing up first, do you have another Hard disk? Or at least a lot of DVDs/Blu-Ray?. Also try to leave some space to SWAP, specially if your computer is old.

 If you have windows, you can use Acronis Disk Manager (but it's paid :( ).

---

### Post by nnamdi on 2008-04-20
thanks i will have to try and give u feed back

---

### Post by the8thstar on 2008-04-20
Swap is unnecessary if you have 1GB or more RAM.

---

### Post by Oldsoldier2003 on 2008-04-20
> **the8thstar said:**
> Swap is unnecessary if you have 1GB or more RAM.

Swap is necessary if you wish to use hibernate and resume, in which case swap must be at least equal to installed ram. Though swap is not used commonly, not having a swap file can create issues with certain applications. Evolution is one of the applications that doesn't handle it well if you are heavily loaded and need to swap but swap isnt enabled. HDDs are so big and so cheap that not having a /swap partition is just silly...

---

### Post by nnamdi on 2008-04-20
yes i have swap it is 2gb beside doest it mean that if i use gparted i lose everything cos am not ready for that man

and i dont have an extra hdd or dvds

i use a hp pavilion dv6000

---

### Post by Oldsoldier2003 on 2008-04-20
> **nnamdi said:**
> yes i have swap it is 2gb beside doest it mean that if i use gparted i lose everything cos am not ready for that man

and i dont have an extra hdd or dvds

i use a hp pavilion dv6000

post the output of sudo fdisk -l so we can see the order of your partitions, also did you want to completely delete the fat32 partition or just resize it?

---

### Post by nnamdi on 2008-04-20
this is what i got

pradeep@pradeep-laptop:~$ sudo fdisk -l
[sudo] password for pradeep:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf74df74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        9726    39062047+  83  Linux
/dev/sda3            9727        9950     1799280   82  Linux swap / Solaris
/dev/sda4            9951       19457    76364977+  83  Linux
pradeep@pradeep-laptop:~$ 


and i want to completely remove the fat32 thank you

---

### Post by nofrendo on 2008-04-20
If everything goes fine, you won't lose any data. I have done this many times and never lost any data. However if you don't REALLY know what you are doing and are following a guide, there is a chance you could mess up and lose data.

---

### Post by the8thstar on 2008-04-25
> **Oldsoldier2003 said:**
> Swap is necessary if you wish to use hibernate and resume, in which case swap must be at least equal to installed ram. Though swap is not used commonly, not having a swap file can create issues with certain applications. Evolution is one of the applications that doesn't handle it well if you are heavily loaded and need to swap but swap isnt enabled. HDDs are so big and so cheap that not having a /swap partition is just silly...

You were right when it comes to hibernation. I personally chose not to waste 2Gb of disk on it, since coming out of hibernation is no faster than a proper boot-up on my laptop (see my sig).

---

