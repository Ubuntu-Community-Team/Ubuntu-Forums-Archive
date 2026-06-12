---
title: "Unable to install from ISO image"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by rlearning on 2007-04-23
I am trying to install x-windows and whether I do it through Aptitude or with an apt-get I keep running into the same problem.  It keeps looking for the ***Ubuntu-Server 7.04 _Feisty Fawn_ ...*** CD.  The problem is that the CD is an ISO image that I got from the Web and it is not labeled like that at all. How do I tell it differently so that I can install x-windows?

---

### Post by bwhite82 on 2007-04-23
You need to edit-out the deb cdrom line in your sources.list:
> 
sudo gedit /etc/apt/sources.list

---

### Post by Cypher on 2007-04-23
You have two options with the .ISO. 1) You can burn a CD to appease Ubuntu, 2) You can mount the ISO (if you already have it in Linux) and point Aptitude to it.

To mount the CD you would do
```

sudo mount -t iso9660 <path/to/ISO/file> /media/<MOUNT>

```

Create a temp directory in the /media directory for this purpose.

Regards

---

### Post by rlearning on 2007-04-23
Soldierboy, I changed the line in the source list to match the label yet now I cannot see the package to install.  I found one on the CD with a very long name for the x11-common (x11-common file.  Is this the file that I need to load x-windows?  How do I tell it that it is located on the CD?****

---

### Post by bwhite82 on 2007-04-23
Alright, try this. First, get rid of that "deb cdrom" line in your sources.list completely. Then mount your ISO like Cipher said, except mount it to /media/cdrom (make sure you have no disks in your CDROM drive).

After you succesfully mount it to that location, from the command line:

> sudo apt-cdrom add

---

