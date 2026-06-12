---
title: "ISO editing program"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2006-09-13
Does anyone know if there is an ISO image editing program for Linux? I would like to be able to edit ISO images, add/remove files and boot images there. I know about UltraISO and MagicISO, but they are for Windows and not free.:(

---

### Post by gigi1234 on 2006-09-13
You don't really need a program to do this in Linux.

Copy the ISO file (filename.iso) to a folder in your directory (like HOME). 

Then make a mount point: mkdir /mnt/ISO (or you could call it anything really).

Then type:

```
mount -o loop -t iso9660 filename.iso /mnt/ISO
```

where "filename" is the name of your file. 

Then, cd /mnt/ISO

You will have mounted the ISO and will be able to copy anything you want from it.

Let me know if this works. I used this method yesterday and it seemed to work fine. 

Cheers!

---

### Post by NT4.0 on 2006-09-16
Thank you for your reply, but it's not actually what I need to do. I learned about this command earlier and already installed Gnome scripts that mount ISOs from the GUI. What I need to do is to be able to edit an ISO file, i.e., change its content (add and delete its files, maybe the boot image too) and save the new version. This is what programs like UltraISO let you do. Of course it's possible to mount an ISO, unpack it into a directory, change the files, and save the new ISO with GnomeBaker, but it's quite a long way, plus it's not possible to change the boot image like this.

---

### Post by smartalecks on 2007-05-25
About a year late, but I'd like to promote this program :)

[http://littlesvr.ca/isomaster/index.php](http://littlesvr.ca/isomaster/index.php)

---

### Post by ramjet_1953 on 2007-05-25
I fully agree with the previous post.

 I would suggest that you have a look at ISO Master.

It works for me and is dead simple to use.

Here's a link to the site:

[http://littlesvr.ca/isomaster/](http://littlesvr.ca/isomaster/)

They have a deb file for dowload that works fine.

Regards,
Roger :cool:

---

