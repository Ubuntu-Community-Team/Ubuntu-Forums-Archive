---
title: "mount point in macbook pro dual boot"
date: 2006-08-18
forum: Apple PPC Users
---

### Post by goneskiing on 2006-08-18
I am trying to leave the mount point of the EFI partition blank as per instructions but get a warning msg of no mount point for partition 1 - will not let me proceed.  Any ideas?

---

### Post by goneskiing on 2006-08-18
Okay, I solve the problem - Here is how:
1) using Dapper 6.06.1 it would not allow me to leave the EFI partition mount point as blank (and gave an error if I left it as the default /media/...
2) I deleted the Linux and swap partitions I set up - you have to then "continue" to apply the deletes, then back up.
3) Back up a step to partitions and choose the option like "choose all available space" - this will automagically create  Linux root ("/") and swap partitions and create the swap space.
4) The setup then proceeds and you follow the instructions as per phico post.

Two more additions to instructions:
a) to synchronize MBR with rEFIt - choose the "Partition Setup" icon along the bottom choices - this will automatically run you thru the synchronization.

b) after you are in linux - to set the display resolution right - run the following:
sudo dpkg-reconfigure -phigh xserver-xorg
select the "1440 x 900" resolution (unless you have 17" then its like 1600 x something)
reboot and enjoy

thanks to phico for excellent instructions - it's nice to have Dapper back again on my MacBook Pro.

---

