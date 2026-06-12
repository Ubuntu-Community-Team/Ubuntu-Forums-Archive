---
title: "Trouble Installing 8.04 from Live CD to 1GB USB flash drive on G4 PowerBook"
date: 2008-08-06
forum: Apple Hardware Users
---

### Post by NomadiusPrime on 2008-08-06
Hi, everybody.  I'm trying to install ubuntu 8.04 onto a flash drive using this guide:

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

I've got my PowerBook G4 booted into Ubuntu 8.04.  I can browse the web with the built-in Firefox and so on.

I am, embarrassingly, stuck on step number 5:

> Now type fdisk -l to list available drives/partitions (note which device is your flash drive Example: /dev/sdb). Throughout this tutorial, replace all instances of x with your flash drive letter. For example, if your flash drive is sdb, replace x with b. 

When I type "fdisk -l", my flash drive doesn't show up, even though File Manager can see it just fine.

I tried to install ubuntu 8.04 to a flash drive about two months ago using a similar guide from pendrivelinux.com, and while I wasn't successful that time, I did at least get past this step.

Help?

---

### Post by tiresia on 2008-08-06
Can you please post what you get just with```
ls -l
```
And just to be sure also ```
ls -l /media
```
Do not forget, that you must run fdisk as root

---

### Post by NomadiusPrime on 2008-08-06
Output from ls -l :

```
root@ubuntu:/home/ubuntu# ls -l
total 0
drwxr-xr-x 2 ubuntu ubuntu 100 1904-01-01 00:42 Desktop
drwxr-xr-x 2 ubuntu ubuntu  60 2008-08-06 19:12 Documents
drwxr-xr-x 2 ubuntu ubuntu  60 2008-08-06 19:12 Music
drwxr-xr-x 2 ubuntu ubuntu  60 2008-08-06 19:12 Pictures
drwxr-xr-x 2 ubuntu ubuntu  60 2008-08-06 19:12 Public
drwxr-xr-x 2 ubuntu ubuntu  60 2008-08-06 19:12 Templates
drwxr-xr-x 2 ubuntu ubuntu  60 2008-08-06 19:12 Videos
root@ubuntu:/home/ubuntu# 
```

Output from ls -l /media

```
root@ubuntu:/home/ubuntu# ls -l /media
total 4
drwx------ 4 ubuntu root 4096 1970-01-01 00:00 SAMWISE
root@ubuntu:/home/ubuntu# 

```

Samwise is indeed the (current) name of the flash drive.

---

### Post by tiresia on 2008-08-07
You should be able to see the flash drive at least with```
df -h
```
Do you want to use your USB drive to start your PowerBook?

---

### Post by NomadiusPrime on 2008-08-07
Yes, that's right.  I'm trying to boot from a 1GB USB flash drive.

Maybe I should reboot the whole machine and just try it all again.

---

### Post by tiresia on 2008-08-07
I have never done that. But I guess that the link you are following works for x86 PC. For an Apple PowerPC don't you need another Partition Map and other FS (using mac-fdisk)?

---

### Post by NomadiusPrime on 2008-08-07
Now that's a good question.  I honestly don't know about the partition mapping.  Hmm.

---

