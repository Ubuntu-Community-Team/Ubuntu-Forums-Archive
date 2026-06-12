---
title: "Snow Leopard and Ubuntu 9.04"
date: 2009-09-06
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-09-06
I will soon be upgrading my Mac OS to Snow Leopard and have seen some posts around issues installing Snow Leopard.  Particularly, the need for a 128mb immediately proceeding the Mac OS X partition.  I dual boot Mac OS X and Ubuntu 9.04 using rEFIt on an intel iMac.

So (being new to Ubuntu) I just wanted to check to see if the following approach is feasible and will not destroy either my current Mac OS X or Ubuntu 9.04 install.

On the internal disk I currently have the following partitions:
/dev/sda1 EFI 200Mb
/dev/sda2 hfs+ (Mac partition) 256.88Gb
/dev/sda3 linux_swap 9.76Gb
/dev/sda4 ext3 /boot 31.25Gb

The approach I was thinking of following is:

1) Boot Ubuntu from live CD
2) Run GPARTED and remove the linux-swap partition
3) Create a new linux-swap partition (preceeded by 128Mb unallocated space)
4) Boot the iMac and startup Ubuntu as normal!
5) Make a backup copy of /etc/fstab
6) do a blkid and note the UUID for the new linux-swap partition
7) gedit /etc/fstab and change UUID to the value for the newly created linux-swap partition
8) reboot the iMac and start up Ubuntu!

I should now be running with the slightly reduced linux-swap partition but importantly now have 128Mb immediately following the Mac OS X partition!

Then I should be able to install Snow Leopard!!!

Does the above sound correct or have I missed something or is the whole idea wrong?

---

### Post by Richardcavell on 2009-09-06
Seems like a good idea.

It might be simpler to delete your existing Linux swap partition altogether.  Let your Snow Leopard DVD do its job.  Then let the Ubuntu installer create a new Linux swap partition. (Which will be identical to the last one).

---

### Post by EvansFive on 2009-09-06
I did not want to run the Ubuntu installer again as I was under the impression that it would blow away my perfectly working Ubuntu 9.04 install...something which has taken me quite a few hours to complete!

How can I run the Ubuntu installer again to create the new linux-swap partition without destroying all my other Ubuntu partitions?

---

### Post by vincebs on 2009-09-07
Would shrinking the Mac partition by 128MB also work?

---

### Post by KaOS-bEat on 2009-10-26
no,


you will get a 

"Mediakit reports no such partition"

when trying to resize the OSX partition.

I have yet to find the correct solution, I will post it here.


Regards

K

---

### Post by maflynn on 2009-10-26
I was able to shrink my HFS+ partition with gparted w/o any such error or problems.  I actually wished gparted could shrink and grow HFS+ partitions so I can have even more flexibility.

---

