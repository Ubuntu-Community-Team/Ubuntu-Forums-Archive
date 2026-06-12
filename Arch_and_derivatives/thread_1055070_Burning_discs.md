---
title: "Burning discs"
date: 2009-01-30
forum: Arch and derivatives
---

### Post by Dr Small on 2009-01-30
I've been trying to burn ISO images to a DVD+RW (for testing purposes, before I actually use just DVD+R) and have got dvd+rw-tools installed, have been using growisofs and the device /dev/scd0 (since that's what wodim detected).

The problem is, I can't get it to blank the Rewritable disc, or write anything to it. I've actually tried every disk device, and none of them work. I've tried:
```
$ growisofs -M /dev/scd0=/dev/zero
:-( /dev/scd0: media is not recognized as recordable DVD: 0
```

And just tried writing the ISO file, too:
```
$ growisofs -Z /dev/scd0=image.iso 
:-( /dev/scd0: media is not recognized as recordable DVD: 0
```

Wodim shows:
```
$ wodim -devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'TSSTcorp' 'CD/DVDW TS-H652L'
-------------------------------------------------------------------------

```

The drive is CD/DVD+RW DL compatible, so it should be working. I even downloaded graveman and tried it, still wouldn't work.

Basically, I'm making copies of non-encrypted (nor copyrighted) DVDs to ISO image files and am trying to make a copy of them by just burning them to another DVD disc. My sister's computer (running Feisty) can burn the ISO image to the DVD (with Nautilus) but I wanted to be able to do it on my system.

Any suggestions, hints or other things I should try?


**edit:** I just looked a bit closer on the front of the drive and it says "DVD-MULTI-RECORDER R DL", so maybe it only can read RW discs and not be able to burn RW discs? I'd try just a plain DVD+R, but I only have a sparing few left, so I don't want to mess up and waste them :(

---

### Post by Neural oD on 2009-01-30
look at the man page for dvd+rw-format

this should do it for u

---

### Post by Dr Small on 2009-01-30
> **Neural oD said:**
> look at the man page for dvd+rw-format

this should do it for u
```
$ man dvd+rw-format
No manual entry for dvd+rw-format
```

---

### Post by Neural oD on 2009-01-30
sorry - that was just to blank out a re-writable - if u want to create the iso - use: growisofs -Z /dev/dvd -R -J /files_that_u_want

if however u want to copy an existing iso onto a disk - i use cdrecord. Look at it's man pages - under examples - and u should come right

---

### Post by Dr Small on 2009-01-30
> **Neural oD said:**
> sorry - that was just to blank out a re-writable - if u want to create the iso - use: growisofs -Z /dev/dvd -R -J /files_that_u_want

if however u want to copy an existing iso onto a disk - i use cdrecord. Look at it's man pages - under examples - and u should come right
Yeah, I tried blanking it with dvd+rw-format and I tried cdrecord, but since apparently the drive can't write to RWs, I'll have to try a DVD+R. I'm guessing that's my whole problem.

---

### Post by Neural oD on 2009-01-30
> **Dr Small said:**
> ```
$ man dvd+rw-format
No manual entry for dvd+rw-format
```


hmmm - strange what version of ubuntu u using

---

### Post by Neural oD on 2009-01-30
> **Dr Small said:**
> Yeah, I tried blanking it with dvd+rw-format and I tried cdrecord, but since apparently the drive can't write to RWs, I'll have to try a DVD+R. I'm guessing that's my whole problem.
Silly of me - I should have checked if your drive had the capacity to write to re-writables
Hope u've solved your problem :)

---

### Post by Dr Small on 2009-01-30
> **Neural oD said:**
> hmmm - strange what version of ubuntu u using
We're in the ArchLinux subforum :p
I'm not running Ubuntu ;)

I'm not going to say that I've solved anything until I try a regular DVD later. But I need to order some more before I do that, since there's only like 3 left.

---

### Post by Neural oD on 2009-01-30
> **Dr Small said:**
> We're in the ArchLinux subforum :p
I'm not running Ubuntu ;)


Heck - sorry about that - just saw the post and posted :( 
I'll be more careful next time - hope u come right though!

---

### Post by jeffathehutt on 2009-01-30
Try writing to /dev/sr0

That's the device I use on my system and it works fine for dvd's or cd's. :)

---

### Post by handy on 2009-01-30
*@**Dr Small**:* In NeroLinux you can simulate a burn, it would be handy if you could do that with whatever burning app's you are using.

---

### Post by smartboyathome on 2009-01-30
> **handy said:**
> *@**Dr Small**:* In NeroLinux you can simulate a burn, it would be handy if you could do that with whatever burning app's you are using.

K3B can do that as well. I think I even remember the option being in Brasero as well, not sure though. :|

---

