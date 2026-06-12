---
title: "What do you type in the terminal if theres a space in a filename?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by ducamie on 2006-12-19
I want to do:

sudo chmod 777 /media/portable drive

but the gap between portable drive is messing it up.

---

### Post by bodhi.zazen on 2006-12-19
Tab completion :p

sudo chmod 777 /media/port<hit tab key here>

will give you:

sudo chmod 777 /media/portable\ drive

Or you can "escape" the white space:

sudo chmod 777 /media/portable\ drive

Or use quotes:

sudo chmod 777 "/media/portable drive"

---

### Post by ciscosurfer on 2006-12-19
> **ducamie said:**
> I want to do:

sudo chmod 777 /media/portable drive

but the gap between portable drive is messing it up.You use a backslash.  For example, if I have a file called  **This is a screenshot.png**, I'd use the following to open it the GIMP```
gimp This\ is\ a\ screenshot.png
```:KSSo in your example, you'd use```
sudo chmod 777 /media/portable\ drive
```

Edit: bodhi.zazen hits it right on the head!

---

### Post by ducamie on 2006-12-19
oh i love you both

---

### Post by ducamie on 2006-12-19
too bad it didnt work lol

my external drive is still read only and has a lock symbol on the folder

---

### Post by ciscosurfer on 2006-12-19
> **ducamie said:**
> too bad it didnt work lol

my external drive is still read only and has a lock symbol on the folderWhat sort of filesystem is on the external drive?

---

### Post by ducamie on 2006-12-19
ntfs

---

### Post by ciscosurfer on 2006-12-19
> **ducamie said:**
> ntfsAre you trying to read and write to the drive?  If so, [you should check out NTFS-3G]("http://ubuntuforums.org/showthread.php?t=217009").

---

### Post by bodhi.zazen on 2006-12-19
Hey, I second that ntfs-3g thing-a-ma-gig :D

---

### Post by ducamie on 2006-12-19
wow thanks again
i'll give that a go now.

jesus i didnt think ntfs would cause such a problem

i blame microsoft %100 as usual

---

### Post by ciscosurfer on 2006-12-19
> **ducamie said:**
> wow thanks again
i'll give that a go now.

jesus i didnt think ntfs would cause such a problem

i blame microsoft %100 as usualIt's not really a Microsoft issue, it's more of an FOSS issue.

---

