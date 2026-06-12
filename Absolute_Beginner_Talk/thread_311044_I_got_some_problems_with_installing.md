---
title: "I got some problems with installing"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Bliz0r on 2006-12-02
Hello, I'm new at this Linux stuff, and decided to try out Unbuntu which I searched on google, and read some stuff about it being friendly to people who want to start with linux.

I burned the CD with ubuntu.(ubuntu-6.10-desktop-i386).

When I put the CD into my driver it loads up normally like any other CD, and loads up the screen. 

BUT! When I reboot to try, the stuff just wont load the CD, it just starts windows up normally. EVEN though I put the BIOS bootlist to load up the CD-rom first, then floppy disk, and then my harddrive. But it dosn't load up the CD at all, it just loads up the windows without giving me any choice at all.

Any idea what's wrong? I so want to try out linux :(

---

### Post by an.echte.trilingue on 2006-12-02
Very common problem.  You probably just burnt the file to the CD rather than making a bootable CD.  Please read t[his article]("https://help.ubuntu.com/community/BurningIsoHowto") to make a bootable CD.

---

### Post by StormNet on 2006-12-02
It could be that you have a bad download-it happens from time to time. If you have the .ISO file still you could run a checksum on the file and see it if it correct.

> b950a4d7cf3151e5f213843e2ad77fe3          ubuntu-6.10-desktop-i386.iso


If you do not have a Windows utility to check md5 checksum, you can use [MD5 Check]("http://www.mgillespie.plus.com/MD5Check.zip") which will compare the file and the checksum you provide (or two files to see if they are identical.) To use it just click on the folder button and locate the ubuntu image (i am assuming that you are using the 6.10 desktop edition) and then paste the checksum value:

```

b950a4d7cf3151e5f213843e2ad77fe3
```

The status panel will let you know if both values are equal.

---

### Post by Bliz0r on 2006-12-02
Thanks alot for the fast replies, I got the stuff working now. :)

---

