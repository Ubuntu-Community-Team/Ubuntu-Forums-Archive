---
title: "Mounting hard drive"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Quan_Chi on 2007-02-27
Ive been trying to mount my 250 gig hard drive

I was told to create a folder, I created the folder and named it 250hd


then I was told to type this

sudo mount /dev/hdb1 /home/quanchi/250hd

first I couldnt do it becuase I wasnt root
I became root and tried it agian
now it says

root@quanchi-desktop:/home/quanchi# sudo mount /dev/hdb1 /home/quanchi/250hd
mount: /dev/hdb1 already mounted or /home/quanchi/250hd busy
mount: according to mtab, /dev/hdb1 is mounted on /tmp/disks-conf-hd

Says its allready mounted, But I cant view the files of the drive....

Not in the folder I created named 250hd and not by simply clicking the drive

when I do try and view the contents of the disk I get this


The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-hdb1".

So I think that it is mounted,
but for some reason i cant view the files on the drive....

How can I view these files?

---

### Post by fdrake on 2007-02-27
try this
sudo nautilus 
write the password
now you shoul be able to see the content of the folder.
to view the folder as a regular user rightclick the folder oh the hd you mounted and click on properties. change the filegroup to yours and select write, read and execute.
let us know.

---

### Post by Quan_Chi on 2007-02-27
I got this

root@quanchi-desktop:/home/quanchi# sudo nautilus

(nautilus:12821): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nautilus:12821): Gdk-WARNING **: locale not supported by C library

(nautilus:12821): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by fdrake on 2007-02-27
well... try this before
sudo apt-get install nautilus 
and
sudo nautilus

---

### Post by STREETURCHINE on 2007-02-27
can you give me the output of

       ```
sudo fdisk -l
```

---

