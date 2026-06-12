---
title: "help: stuck in text mode"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by angelgrimm on 2008-02-25
Stuck in text mode. 
I was messing with synapctics, trying to get some flash pages to run right on firefox, and when i rebooted the pc it sent an error:

Loading, pease wait...
Kinit: name_to_dev_t(/dev/disk/by-uuid/3c7a8f65-b709-494a-92f1-318a38220def)= sda5(8,5)
kinit: No resume image, doing normal boot... 

Nothing, recovery mode nothing, startx gave a gray screen with a mouse pointer
So after a lot of searching, and trying many things (dpkg-reconfigure xserver-xorg didn't do a thing), FINALLY, I read something about swaping off/on the ram (swapoff /dev/sda, mkswap /dev/sda, then update -initramfs -u) and it worked... sort of...
Now my pc loads fine, it says:

Starting up...
Loading, please wait...
Ubuntu 7.10 mypcname ttuy

then asks for my login.... still under text mode ](*,)

Just tried : sudo aptitude update/upgrade (asked me to run dpkg --reconfigure -a, then ran fine), startx.... and i still get gray screen with mouse pointer....

I would do a reinstall, as I already backed up my info, except for evolution mails. I don't know how to get them out (I mean, in win you could just copy the dbx files and paste them) :-k. 

Any help? Either getting the mails out or correcting the problem would be fine by me....

---

### Post by taurus on 2008-02-25
All your personal settings is in $HOME.  So, you should have a look at ~/.evolution.

```
cd ~/.evolution
ls -la
```
Looks to me like somehow the UUID for your / has changed!  Look in /boot/grub/menu.lst, /etc/fstab, and /dev/disk/by-uuid to make sure the UUID matches for /--root filesystem.

```
sudi fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
ls -la /dev/disk/by-uuid
```

---

### Post by angelgrimm on 2008-02-25
that's sounds good... 
ok, done all that, what should I be looking for?

---

### Post by kryth on 2008-02-25
all else fails you can try to reinstall the gnome desktop.

sudo apt-get install ubuntu-desktop

good luck

---

### Post by uidb4056 on 2008-02-25
> **angelgrimm said:**
> that's sounds good... 
ok, done all that, what should I be looking for?

you should check that the uuid of the partitions matches in /etc/fstab and /boot/grub/menu.lst with the contents of the command blkid. If some mismatches edit it to reflect the values showed by blkid.

---

### Post by angelgrimm on 2008-02-25
actually reinstalling the ubuntu desktop did the trick....

tnx to all

---

