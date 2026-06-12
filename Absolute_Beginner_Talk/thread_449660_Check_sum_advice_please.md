---
title: "Check sum advice please"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-20
I have just downloaded a DVD ISO and would appreciate advice on how to perform a Checksum using ubuntu.

I tried to understand the STICKY but I felt that the posting expected a level of linux knowledge that I do not posess.

Could somebody please give me an idiot's guide on how to do this?

Cheers

---

### Post by taurus on 2007-05-20
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by the lemming on 2007-05-20
> **taurus said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As I said, I've read the link but do not understand what to do.  The article seems to require a level of skill that I do not posess.

---

### Post by Ozeuss on 2007-05-20
go to Applications-> accesories-> open Terminal
you type the commands in there. type "md5sum" space, and then you can just drag the file onto the terminal and it should appear inside quotation marks. click enter.
it will output a series of digits- you should compare it to a hash list to see if ti matches.

---

### Post by the lemming on 2007-05-20
I did as requested but instead of a bunch of numbers a new window opened asking for a new location.

Now I'm really confused

---

### Post by Kobalt on 2007-05-20
Check [this]("http://psychocats.net/ubuntu/iso#checksum") out for some detailed explanations on checking the md5sum.

---

### Post by the lemming on 2007-05-21
> **Kobalt said:**
> Check [this]("http://psychocats.net/ubuntu/iso#checksum") out for some detailed explanations on checking the md5sum.

I tried the link and I'm a bit confused.  It looks like the instructions are for Windows and not Linux, is that correct?

If that is the case then I would appreciate help doing the checksum using ubuntu.  I'm trying to wean myself off my dependancy for XP.  It would be far simpler to boot back into XP to do stuff but I would have missed an opportunity to discover something new about working with ubuntu.

Cheers

---

### Post by mocqueanh on 2007-05-21
Are you saying: checksum MD5 when you use Ubuntu, not Windows ?

Assumed that file.iso and file.iso.md5 are in the same folder
```
md5sum -c file.iso.md5
```

---

### Post by Ozeuss on 2007-05-21
let's try from fresh.
first you need to browse through the terminal to the folder where you downloaded the file. actually, it will probably me more convenient if you move the .iso file to your home folder. then you won't need to navigate, just open the terminal.
now in terminal you type:
```
md5sum <nameof isofile>.iso
```
for instance, if i have a gparted iso and i want to check it, i will type
```
md5sum gparted-livecd-0.3.4-6.iso
```
that will output:
```
faf4b410ecb2f504cd077648e79c7d92  gparted-livecd-0.3.4-6.iso
```

same process should apply to the dvd iso you downloaded.

---

### Post by mrcanard on 2007-05-25
[QUOTE=Ozeuss;2693763]let's try from fresh.

Thanks, That works great.

---

