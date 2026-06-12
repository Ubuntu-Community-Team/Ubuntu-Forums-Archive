---
title: "How to read from/write to XP drive with Gutsy"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2007-11-25
How can I use ntfs-3g to read from and write to the /dev/sda1 on my laptop?
I can open the sda1, see the folders, open them but most result in "No application suitable for automatic installation is available for handling this kind of file."  I'm using Gutsy fully updated on a laptop.
Thanks for any help I may receive. Jim

---

### Post by LaRoza on 2007-11-25
You should be able to read an write to the NTFS drive.

If you are trying to running Windows applications, Wine will handle some of them, but not all.

What type of file gives that warning?

---

### Post by rtrdom on 2007-11-25
Thank you for the response, LaRoza
Some of the file types that yield the aforementioned result are: fmp, dll, exe, dat, drv,
among others.  I wish to open and use a program called Paperport which is on the XP drive while I am working on the Ubuntu drive. The reason...I know of no software that
will permit me to pull up a photo or document, make notes on it, and then save it, that
is Ubuntu friendly.  I hope you or someone does as I would like to stay away from
Windows as much as possible.
Respectfully,
Jim

---

### Post by LaRoza on 2007-11-25
> **rtrdom said:**
> Thank you for the response, LaRoza
Some of the file types that yield the aforementioned result are: fmp, dll, exe, dat, drv,
among others.


Why are you trying to open those files? They are not useful for Linux, and are used (and are) Windows programs. It is possible to open them (in a hex editor) but that is not want you want.

You can try installing the program you want in Wine.

I don't know anything about such programs, but you should create a thread on it.

---

