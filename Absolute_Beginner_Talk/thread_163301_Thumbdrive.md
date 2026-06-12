---
title: "Thumbdrive"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by arsenik on 2006-04-20
I know this is a total newb question, but when i plug my thumbdrive in to ubuntu it detects it and puts a link to it on my desktop.  How do I access the thumbdrive from the command line/terminal window?

---

### Post by Ecthelion on 2006-04-20
You can use
```
ls /media/**namethumbdrive**/
```
to display the contens

just accessing it is
```
 cd /media/**namethumbdrive**/
```

---

### Post by Qrk on 2006-04-20
The drive is mounted in /media and is usually in a folder starting with UDISK, although the name can change. 

```
ls /media

``` 

to find the drive, To open it, us cd. For me, I do:

```
cd /media/UDISK\ 20X/
```

---

### Post by arsenik on 2006-04-20
thanks and sorry for the stupid question. I was looking in /dev/

---

### Post by bigpup on 2006-09-04
My USB thumbdrive appears as "UDISK 2.0"
I can browse it in Nautilus, but I cannnot CD into it, in Terminal.
Whatever name I try returns "No such file or directory"
What do I call it?

---

### Post by breuerp on 2006-09-04
If it automounts it for you it will be listed as a subdirectory of /media.  Linux handles spaces in filenames differently than Windows.  Try:  cd /media/US [tab] to let tab completion fill in the rest of it for you.

---

### Post by bigpup on 2006-09-04
Thanks. TAB worked, filling in "/media/UDISK\ 2.0/".
The prompt in Terminal is shown: "media/UDISK 2.0$"

:-D

---

