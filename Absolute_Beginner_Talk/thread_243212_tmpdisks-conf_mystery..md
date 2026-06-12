---
title: "/tmp/disks-conf mystery."
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by 2frykai on 2006-08-24
Hello,

I've got 2 SATA hard disks in my computer. One came with the computer and has Windows XP on it. The other one: I put in and installed Ubuntu on it. 

In Ubuntu, the Discs Manager (System > Administration > Discs) shows the other hard disk and shows the NTFS partition has an "Access Path" of /tmp/disks-conf-sda2. The status is set to "Accessible". 

But Ubuntu won't allow me to Browse this folder. 

Why does Ubuntu "mount" my ntfs folder there? Or is it a copy? Can I delete it? 

Running "df" says that I'm using 100GB of space because of that folder :(

Thanks in advance.
2frykai

---

### Post by aysiu on 2006-08-24
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by 2frykai on 2006-08-25
Hi,

Thanks for the reply. I managed to get NTFS mounted properly: once there is a proper entry in the /etc/fstab, then the Disc Manager seems to cooperate.

/2fry

---

