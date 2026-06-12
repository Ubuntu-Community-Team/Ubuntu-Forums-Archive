---
title: "URGENT, how do i move docs into Flash drive, need persmission"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-09-20
hey ive got to hand this document in by 4 o clock, its 3 clock now, i need to move the bloody document into my flash drive, its mounted and everything, but i cant drag and drop into it, how do i do this in the terminal, i dont have much time, i tried mv document /media/MY DATA it says no such directory, the flash drive is called MY DATA btw

Please someone hlep i got to do this otherwise ill fail my assignment!!!!

---

### Post by Pumalite on 2007-09-20
At the Terminal:
sudo chmod 777 /dev/xxx
(xxx to be replaced by you)

---

### Post by Dr Small on 2007-09-20
Try
```
mv /home/USER/path/to/file/document /media/MY\ DATA
```

---

### Post by dynamethod on 2007-09-20
xen@xen:~/Desktop$ sudo mv /home/xen/Desktop/Assignment5ET600.doc /media/MY\ DATA
mv: cannot create regular file `/media/MY DATA/Assignment5ET600.doc': Read-only file system

---

### Post by dynamethod on 2007-09-20
xen@xen:~/Desktop$ sudo chmod 777 /dev/xen
chmod: cannot access `/dev/xen': No such file or directory

---

### Post by Dr Small on 2007-09-20
Ok. So we now know that my method will work if you have proper permissions on the flash drive. 

So, now try:
```
sudo chmod 777 /media/MY\ DATA
```

---

### Post by Pumalite on 2007-09-20
It seems you have to change /dev/xen for /dev/???

---

### Post by dynamethod on 2007-09-20
xen@xen:~$ sudo chmod 777 /media/MY\ DATA
chmod: changing permissions of `/media/MY DATA': Read-only file system

still cant drag and drop files into Flash Drive :S

---

### Post by Dr Small on 2007-09-20
The only times I have ever got " Read-only file system" errors were when my flash drive was corrupted and was bad...

---

### Post by Pumalite on 2007-09-20
It must be ntfs.

---

### Post by Dr Small on 2007-09-20
Have a floppy or cd at hand? You may need it.

---

### Post by dynamethod on 2007-09-20
yeah the Flash drive is NTFS, its ok though i just hit up my flatmate using his flash drive instead, thanks for help though guys :)

looks like my flash drive is buggered :S

---

### Post by Dr Small on 2007-09-20
You can always reformat it to fat32 with gparted to be compatible with both Ubuntu and Windows ;)

---

