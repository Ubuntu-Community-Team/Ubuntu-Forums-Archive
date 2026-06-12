---
title: "Ext3 permission denied on Hard Drive"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by MantinoX on 2008-01-24
ive searched many topics and still need help.
I reformatted one of my Hard Drives to ext3 formate and when i mount the drive i get permission denied to write data etc....

What is need to be done so that i can transfer my files back onto my hard drive?
Hd is an internal Sata

---

### Post by taurus on 2008-01-24
Since it's an ext3 filesystem, just change the ownership of /media/disk from root to your login name, Mantino.

Applications -> Accessories -> Terminal
```
sudo chown -R Mantino:Mantino /media/disk
ls -la /media/disk
```

---

### Post by mikeyphi on 2008-01-24
From the thumbnail it seems that you are trying to access the Lost & Found folder....this is a system folder that you don't have access to!!!

Try to get to the disk not to /disk/lost & found

---

### Post by MantinoX on 2008-01-24
mantino@mantino-desktop:~$ sudo chown -R Mantino:Mantino /media/disk
[sudo] password for mantino:
chown: `Mantino:Mantino': invalid user
mantino@mantino-desktop:~$ 


is what I get

Is there something im forgetting to do?

---

### Post by taurus on 2008-01-24
```
sudo chown -R mantino:mantino /media/disk
```
I thought it was Mantino from your screenshot.

---

### Post by mikeyphi on 2008-01-24
Use mantino NOT Mantino....perhaps?

---

### Post by MantinoX on 2008-01-24
mantino@mantino-desktop:~$ sudo chown -R mantino:mantino /media/disk/ ls -la /media/disk
chown: invalid option -- l
Try `chown --help' for more information.
mantino@mantino-desktop:~$

---

### Post by taurus on 2008-01-24
They are two separate commands, one on each line.

```
sudo chown -R mantino:mantino /media/disk      #Return key
ls -la /media/disk     #Return key
```

---

### Post by MantinoX on 2008-01-24
Ok From here i get
[COLOR="SeaGreen"]mantino@mantino-desktop:~$ sudo chown -R mantino:mantino /media/disk
mantino@mantino-desktop:~$ ls -la /media/disk
total 24
drwxr-xr-x 3 mantino mantino  4096 2008-01-24 15:36 .
drwxr-xr-x 7 root    root     4096 2008-01-24 17:20 ..
drwx------ 2 mantino mantino 16384 2008-01-24 15:36 lost+found
mantino@mantino-desktop:~$          
[/COLOR]
                             
I take it that all i need to do?

Also Thank you for the time and patients on this for me You been such a good  help.

---

### Post by taurus on 2008-01-24
Now, you are the sole owner of /media/disk.  See if you can copy something to /media/disk.

---

### Post by MantinoX on 2008-01-24
Nevermind everthing is dandy!

thanks alot!!!!

---

### Post by biojc2 on 2008-06-05
Finally, somebody knows what he was doing. Excelent info. Helped me a Lot. Thanks.

---

