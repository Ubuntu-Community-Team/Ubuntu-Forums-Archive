---
title: "Making LiveCD's"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-08-24
Today I'm going to buy a DVD+RW/CD+RW. I plan to burn a few LiveCD's to give out at a function later. Which brand (writer and cd) should I buy? And how do I go about making copies of my LiveCD? I've been searching for a comprehensive how-to thread but to no avail.

Thanks in advance! :)

---

### Post by Dr Small on 2007-08-24
I don't know about what brand to get of a DVD rom, but to make an ISO out of your current LiveCD, run this command with the LiveCD in.

```
dd if=/dev/cdrom of=ubuntu-7.04-desktop-i386.iso 
```
(You may have to change cdrom to cdrom0 or something if it doesn't work)

Dr Small

---

### Post by az on 2007-08-24
> **Nessa said:**
> Today I'm going to buy a DVD+RW/CD+RW. I plan to burn a few LiveCD's to give out at a function later. Which brand (writer and cd) should I buy? And how do I go about making copies of my LiveCD? I've been searching for a comprehensive how-to thread but to no avail.

Thanks in advance! :)

Boot Ubuntu.  Put the live cd (or any other cd you want to copy) in the drive.  When the icon appears on the desktop (forget about the other stuff that will pop up regading the packages on the cd...) right-click on it.

Click on copy.

copy the cd.  You can copy it to file and that will make an iso image out of it, if you want.

You can also copy a cd using gnomebaker of K3B....

---

### Post by Nessa on 2007-08-24
Does it make an iso image automatically?

---

### Post by Dr Small on 2007-08-24
Which one?

---

### Post by Nessa on 2007-08-24
Copying it to a file...is that an iso or do I have to convert it or something?

Also, the device should be plug and play right?

---

### Post by armandh on 2007-08-24
I like the memorex  16X 2L DVD+R
[http://www.memorex.com/](http://www.memorex.com/)

---

### Post by funrider on 2007-08-24
FYI, do you know you can order free installation CD from ubuntu.com website? BTW, why do you need DVD? the iso is less than 700MB.

---

### Post by Nessa on 2007-08-24
I want to give out ubuntu cd's later tonight. Ordering takes a month or so. I know I don't need the dvd+rw part but I just want that option in the future.

---

### Post by az on 2007-08-25
> **Nessa said:**
> Copying it to a file...is that an iso or do I have to convert it or something?

Also, the device should be plug and play right?

The file that it will make will already be an iso.

The device being the cd drive?  Yes.

---

