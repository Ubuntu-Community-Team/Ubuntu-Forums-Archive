---
title: "Can't delete files on Desktop"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Stupojohn on 2007-05-30
Using Xubuntu, I unzipped a folder full of pdf's onto the desktop and now I can't delete any of them!
If I right-click on them, "Delete" is in gray, and under properties it says "Access: read only".
How can I delete them (or at least put them somewhere less obtrusive)?  Thanks in advance!

---

### Post by daimaru on 2007-05-30
kind of weird but u sure can get rid of them by opening a terminal (applications-->accessories-->terminal)
and typing in :
```
cd
cd Desktop
sudo rm something.pdf
```
or if u only got pdfs on desktop that u want to delete (all of them)
```
sudo rm *.pdf
```

if u as a user want to be able to have access to those files (which u should already have ??) you could just change their permissions by typing in console (@desktop) #
```
sudo chmod 777 pdfFileName.pdf 
```
then you should be able to do anything with them

---

### Post by jrmwvu04 on 2007-05-30
One way would be to delete them as root with Thunar. Hit Alt+F2 and run:

```
gksudo thunar
```

Navigate to the files (/home/<your username>/Desktop) and delete them.

---

### Post by Stupojohn on 2007-05-30
Thanks daimaru and jrm.  All of these solutions worked perfectly! (Yeah, I tried them all).
This is definitely getting written down in the "stuff I need to remember" folder.

---

### Post by jfinkels on 2007-05-30
> **Stupojohn said:**
> Thanks daimaru and jrm.  All of these solutions worked perfectly! (Yeah, I tried them all).
This is definitely getting written down in the "stuff I need to remember" folder.

It'll become second nature after a short time :D

---

