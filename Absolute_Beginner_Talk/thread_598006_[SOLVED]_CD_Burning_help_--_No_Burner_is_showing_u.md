---
title: "[SOLVED] CD Burning help -- No Burner is showing up"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by adidalax on 2007-10-30
Hey all,

Just wondering if there's any special package to make cdburing work. I have a standard NEC DVD burner and have tried the nautalis based prog as well as tried installing Brasero. Both of them only allow me to "burn" an image to disk and aren't showing my burner. The wierd thing is that if you go to Places -> Computer, it is showing as a CD-RW / DVDRW drive....

Here's the output from running cdrecord -scanbus:

```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
scsibus0:
        0,0,0     0) 'ATA     ' 'ST3160812AS     ' '3.AA' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus1001:
        1001,0,0 100100) '_NEC    ' 'DVD_RW ND-3550A ' '1.05' Removable CD-ROM
        1001,1,0 100101) *
        1001,2,0 100102) *
        1001,3,0 100103) *
        1001,4,0 100104) *
        1001,5,0 100105) *
        1001,6,0 100106) *
        1001,7,0 100107) *
```

Are there any specific packages I need to install or something to make this work or is this a configuration issue? Any help is much appreciated.

---

### Post by MrFSL on 2007-10-30
Well essentially all the different burning apps for Ubuntu (K3B, GnomeBaker, Brasero, Nautilus) all use the same command line tools to do the work. I have seen GREAT success using these apps and they are all VERY impressive.

That being said - there have been times where these apps simply have not done what I needed them to do. For a very small and very reasonable and fee you might want to buy a copy of nero for linux:
[http://www.nero.com/eng/store-linux.html](http://www.nero.com/eng/store-linux.html)

It is very nice and free to try. Plus it supports alot of features not normally found in other linux based burning applications.

---

### Post by adidalax on 2007-10-30
Well, I mean its not really an issue of not having a feature, more just that it's not "detecting" my burner correctly or something. That's why I was hoping it was a matter of installing a package or setting up a config somewhere....

---

### Post by MrFSL on 2007-10-31
Are you receiving any particular error message in Brasero or is it only allowing you to burn to File Image?

---

### Post by adidalax on 2007-10-31
Okay.....wierd.....I rebooted w/ the blank CD in the drive and now it looks like it's going to work fine. I actually get the option to burn to CD...heh :confused:

Whatever.....thanks for the help :-P

---

