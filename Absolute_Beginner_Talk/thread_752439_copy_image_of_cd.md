---
title: "copy image of cd"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by xstation on 2008-04-11
to copy the image of a disk from cdrom drive (actually it also appears on my desktop to a file 
in the home directory is the cp command?


xstation

---

### Post by herbster on 2008-04-11
To make an ISO image you can use K3b.

```
sudo apt-get install k3b
```

---

### Post by aeiah on 2008-04-11
unmount the cdrom drive and do this in the terminal:

```
dd if=/dev/cdrom of=cd.iso
```

change cdrom to whatever it is. it might be /dev/dvd or something.

---

### Post by kostkon on 2008-04-11
> **xstation said:**
> to copy the image of a disk from cdrom drive (actually it also appears on my desktop to a file 
in the home directory is the cp command?


xstation
Simply, if you right click on it you will find an option to write the CD/DVD to the hard disk. If you select it an ISO image of the CD/DVD will be created.

---

### Post by aeiah on 2008-04-11
haha, or that, of course. shows how often i put a disc in my drive i guess :confused:

---

