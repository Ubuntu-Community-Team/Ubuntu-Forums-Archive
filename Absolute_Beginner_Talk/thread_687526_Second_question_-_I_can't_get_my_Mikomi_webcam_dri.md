---
title: "Second question - I can't get my Mikomi webcam drivers to work."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by DayOldPorridge on 2008-02-04
Okay, so I tried running the installation program from the drivers CD under Wine, but it just closes after running into some kind of error, so I'm not really sure what to do.  :S  I tried Googling and it seems as if a few other people have this problem but there isn't really an answer about how to fix it.  Any ideas as to where I could get these drivers?

It's a Mikomi M6225.

---

### Post by DayOldPorridge on 2008-02-04
Bumpity bump.

---

### Post by DayOldPorridge on 2008-02-04
Bump.  >_>;

---

### Post by DayOldPorridge on 2008-02-04
Bump.

---

### Post by DayOldPorridge on 2008-02-04
Bump.

---

### Post by vermoos on 2008-02-08
ooof! my webcam is mikomi m6517z >_<

lsusb --> Bus 002 Device 005: ID 0c45:612e Microdia

don't know what to do... help!

sincerely

---

### Post by vivalant on 2008-02-08
Have you tried the Generic SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) ?

---

### Post by intel on 2008-02-11
Microdia 
(Webcam Support group for all Microdia chipsets under Linux)
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam

0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105

(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 
All of the above webcams are unsupported under Linux

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

Please join this Group, to help each other get better support for these webcams from Linux.

---

