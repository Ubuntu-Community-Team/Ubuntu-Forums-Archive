---
title: "Absolute newbie (about 15 mins) help needed re: gunzip"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by chuffy on 2006-11-28
I'm trying to use an old PC as Network Attached Storage at work just to store a few common files on.

I have found a product that's free called NASLite but it works from a compressed floppy disk (1.722 MB on a 1.44MB). This can't be created from windows, but on the NASLite website it states that a bootable floppy can be created from Linux using:

gunzip NASLite.img.gz
fdformat /dev/fd0u1722
dd if=NASLite.img of=dev/fd0u1722

I don't actually know how to do this. I am currently running this laptop on a live CD version of Ubuntu to see if I can work it out - I can't.

Any help greatly appreciated.

I have been considering Ubuntu for some time and this is my foray into it so thanks in advance...

---

### Post by jimbren on 2006-11-28
Open up a terminal window and then browse to the directory where you downloaded the file.  Most likely it is /home/Desktop

Then enter the commands you posted, and you should be good to go.

jimbo

---

### Post by xyz on 2006-11-28
If you really are a 15-minute new Linux user, I'll just throw this in!
Sorry if you already knew this!
To open a terminal, go to Application > Accessories > Terminal
This will open what's called a terminal
In that (window) called a terminal, type:
```
cd //home/Desktop
```
the "cd" thing will take you to your Desktop where ,I assume, the folder you want to gunzip is!
Fell free to come back and ask more questions and WELCOME!

---

### Post by eXisor on 2006-11-28
There is a windows based program that'll let you write a bootable image (img file) to a stiffy. It's called rawrite (the dos version) and rawritewin (a gui version). They commonly come in a package called dosutils. (A google should turn something up).

---

### Post by chuffy on 2006-11-28
Thanks folks, will try in a bit - sadly got work to inbetween tinkering.
XYZ, I didn't know how to get to the desktop from a terminal (I really am that new).
I did try RawWrite (from freshmeat) but it wouldn't work, so took the opportunity to try Linux. Have installed Ubuntu before but it didn't like the hardware - it was a couple of years ago so went back to the dark side.
If there were thanks buttons, I'd click 'em all - unfortunately you'll have make do with this, so - thanks again.:KS

---

