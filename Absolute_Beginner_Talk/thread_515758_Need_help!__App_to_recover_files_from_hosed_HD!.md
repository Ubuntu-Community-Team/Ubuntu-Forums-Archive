---
title: "Need help!  App to recover files from hosed HD!"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-08-02
One of my HD's crapped out.  It has bad sectors for sure, SMART reports imminent death, but is still readable.  It is very slow to read files, and some are gone, but many are there.  Ubuntu freaks out when it tries to mount it, Windows seems to be able to mount it most of the time.  Both do see it connected.

Is there an application out there that can look at the HD and recover files from it while ignoring read errors?

---

### Post by milosz.galazka on 2007-08-02
Hello,

At first you should create image of that disk (dd). Then you can check The Coroners Toolkit, The Sleuth Kit or other forensics tools included in package repository.

---

### Post by click4851 on 2007-08-02
+1 to what milosz said. I would recomend a liveCD like INSERT or GParted to help with recovery.

---

### Post by Atomic Dog on 2007-08-02
OK thanks for the tips.  I will investigate and download, hopefully I can salvage some more files off this drive.  Looks like these apps have promise!

Thanks again!

---

### Post by Atomic Dog on 2007-08-02
Not familiar with dd.  It looks like I could pipe it through gzip so I could write it to my portable usb drive.  Is that a good move or should I try to pipe the image to a clean new hard drive?

---

### Post by milosz.galazka on 2007-08-02
Hello,

dd is quite easy for basic use

dd if=/dev/bad_disk of=/file/or/device

There is also *bs* parameter that would greatly speed up things but i don't know how it would behave in this situation, you can check transfer rate with different values...

If you wish to use dd to transfer data excactly to new hard disk as device remember about sizes of both devices.

---

### Post by Atomic Dog on 2007-08-02
> **milosz.galazka said:**
> Hello,

dd is quite easy for basic use

dd if=/dev/bad_disk of=/file/or/device

There is also *bs* parameter that would greatly speed up things but i don't know how it would behave in this situation, you can check transfer rate with different values...

If you wish to use dd to transfer data excactly to new hard disk as device remember about sizes of both devices.

Oh good.  Thank you.  I should be home in 5 hours.  Looks easy to use, and I do have a larger HD that I can dump the contents into.  If this works, and I don't know how it will deal with bad files, but it's worth a shot!.  Thanks!!!

ps.  Should I use the noerror switch?  Or should I try it without it?

---

### Post by milosz.galazka on 2007-08-02
If new disk is bigger then I suggest you to create image in file. If there are errors then dd will just stop without noerror switch  so it could be bad if you go to sleep ;p

with noerror switch it will go further but I don't know if it will save 0 or maybe 1 or just skip?

---

### Post by splintercellguy on 2007-08-02
TestDisk might be of interest, dd is great too.

---

### Post by milosz.galazka on 2007-08-02
dd is just for creating backup of data so you can work on copy

by the way thanks for mentioning TestDisk as it looks like very interesting tool

---

### Post by Alterax on 2007-08-02
I use the Helix liveCD for this kind of work.  There's a tool on it called Foremost (it's a CLI tool, so do some reading up on it first before you try it), but I use it to mainly recover documents, zip archives, and multimedia files.

It may be just what you are looking for, if you're not afraid of a command line (and your original post leads me to believe that you aren't.)

---

### Post by ramjet_1953 on 2007-08-02
I have great success at recovering data from failing HDD's with [COLOR="Blue"]SpinRite[/COLOR] for several years.

It is an iso that you burn to a CD and then boot from it.

It is not free, but does a great job and whether it is worth it to you, depends upon the value of the data that you need to recover.

It can be used for virtually any OS.

Here is the link to the site:

[http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm)

Regards,
Roger :cool:

---

