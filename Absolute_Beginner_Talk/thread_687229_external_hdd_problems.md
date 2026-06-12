---
title: "external hdd problems"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Nolander on 2008-02-04
i bought a external hdd case 2day, and i put a old 40gb hdd. now i wanna reformat it, i dont know how. how do i find the name eg. hda1... and wat should i use to reformat it?

-nolander

---

### Post by ichbinesderelch on 2008-02-04
when the hdd is plugged in do a "dmesg" and watch for some output like /dev/hda(hda is likely to be your first harddrive in the computer, i guess it would rather bin hdc odr hdb!), if you wanna do it very easily apt-get install qparted, graphical programm for doing all this, you don't even need the dmesg thing for that

---

### Post by Nolander on 2008-02-04
im running fluxbuntu so i dont get a message. and i cant install qpart.

-nolander

---

### Post by indytim on 2008-02-04
I have an external 320G SATA.  I found the easiest way to format it was to get a copy of GParted Live.  Boot to GParted Live WITH your external HD plugged in.  In  GParted, find your drive and partition as you need to (I partitioned it to ext3).  

That's it... no pain.... no mess:)

IndyTim

---

### Post by Nolander on 2008-02-04
i installed gparted but it doesnt find the device, ill try a different hdd.

-nolander

---

### Post by SpiderGorilla on 2008-02-04
Try this:

Open terminal, type in:

fdisk -l

(make SURE that the -l is on there. That's a lower-case L not a capital i! Paste the results of what it returns. Type in NOTHING beyond -l !

---

### Post by Nolander on 2008-02-04
when i run gparted in the terminal it has,
```
Unable to open /dev/hda read-write (Read-only file system).  
/dev/hda has been opened read-only.
Unable to open /dev/hda - unrecognised disk label.
```

-nolander

EDIT: fdisk -l only shows my lappys HDD

---

### Post by ichbinesderelch on 2008-02-04
did you run gparted as root?

---

### Post by Nolander on 2008-02-04
yes

---

### Post by hyper_ch on 2008-02-04
use

```

sudo fdisk -l

```

---

### Post by Nolander on 2008-02-04
i ran that it only show my laptop hdd.

---

### Post by ichbinesderelch on 2008-02-04
are you sure you plugged your hdd correctly in the hdd case? is it recognized on any other pc?

---

