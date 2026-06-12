---
title: "Doesn't recognise modem"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by lila on 2005-11-27
Hello, 
absolute newbie - new to Linux in general, Ubuntu in particular, new computer (thought I'd do a clean break - last one, Win98, died, hard disk failure).  Not particularly computer literate.  Willing to learn though.  

The installation went ok so far, the coputer recognises most of its hardware.  Tried a few distributions as well, this one is the first that works.  Love it!  And this forum (collection of forums)!

However, the computer doesn't seem to recognise a modem, so here I am on a Sunday using a computer at work to type this...  Now, I have a CD that came with it which is called "motherboard drivers".  I can open the CD, it has all sorts of files and folders on it, and all the drivers I could want, complete with a folder in each folder that says "Linux" (as well as various Windows versions) - but when I click on these (the Linux ones), they just seem empty.  In fact, all the folders seem to be empty.  The CD has one file that is called "start-up", which would be what I'd try to run, except it's .exe and I've just learned by reading old threads that I can't. (I did try).

I think once I can access the internet from home with Ubuntu, life will get easier because I can then access all the help and how to things available.  Any ideas on how to get that modem going?  I don't even know any name or serial number for it.  All I know is that the computer is supposed to have one, and there are things in the box that look like they could be one.  And once it recognises it, how (or rather where, in what) do I set up my dial-up account?

Curiously, it DOES recognise (as did the other distributions I tried) a floppy disk drive.  It doesn't have one.  I looked, there definitely isn't a physical floppy drive.  Could there be a software-floppy drive, and if yes, what's the point, seeing that you can't put a floppy into it?

Any help would be greatly appreciated.  I'll make a cup of tea (I don't know what the caffeine rating is of that...  I hope it's not an illegal substance in the Linux universe!) and hope someone has an idea before I have to go home again...

Cheers, Lila

---

### Post by ssam on 2005-11-27
it is possible that you have a software modem. have a look at
[http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html](http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html) and [http://en.wikipedia.org/wiki/Winmodem](http://en.wikipedia.org/wiki/Winmodem) .

the quickest way to check is to open a terminal. applications -> acessories -> terminal. and run the command
```
wvdialconf /dev/null
```
wvdial will have a good look to see if you have a hardware modem. (the /dev/null bit tells it not to make a configuration file.)

i would not worry much about it thinking there is a floppy drive. it may just assume that there is one without checking.

tea is ok.

---

### Post by lila on 2005-11-27
[QUOTE=ssam]it is possible that you have a software modem. have a look at
[http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html](http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html) and [http://en.wikipedia.org/wiki/Winmodem](http://en.wikipedia.org/wiki/Winmodem) .

the quickest way to check is to open a terminal. applications -> acessories -> terminal. and run the command
```
wvdialconf /dev/null
```
wvdial will have a good look to see if you have a hardware modem. (the /dev/null bit tells it not to make a configuration file.)

i would not worry much about it thinking there is a floppy drive. it may just assume that there is one without checking.

tea is ok.[/QUOTE]


Thanks a lot!  Feel like I have a chance of getting somewhere... Did the wvdialconf thing (my first ever command line!), which came up with "there is no modem" (or words to that effect).  So, no hardware modem.
Have visited the website, copied the scanModem programm + instructions.  However, it tells me to copy the programm into my directory using mcopy a:scanModem.gz.  which I have tried, I assume I'm supposed to do this in terminal, but it comes up with "command not found".  Is this due to the sudo versus root thing I have read about?  How do I copy a file from a CD into my directory?

---

### Post by ssam on 2005-11-27
looks like you got old instructions. ([http://www.ma.utexas.edu/cgi-bin/man-cgi?mcopy](http://www.ma.utexas.edu/cgi-bin/man-cgi?mcopy)) it seems that mcopy is just a way of getting files of msdos disks, but you should have been able to do that quite easily.

you just need to  get the scanModem.gz into your home folder and then carry on from there.

if you have put the file on a cd-r then when you put the cd into you linux computer it should popup, then you can drag it to your home folder. (the same should happen with a floppy disk or usbstick).

if this is not happening, but it works with other cds (like the ubuntu install cd) then maybe you need to fixate/finalise the cd you burned.

---

### Post by lila on 2005-11-28
[QUOTE=ssam]looks like you got old instructions. ([http://www.ma.utexas.edu/cgi-bin/man-cgi?mcopy](http://www.ma.utexas.edu/cgi-bin/man-cgi?mcopy)) it seems that mcopy is just a way of getting files of msdos disks, but you should have been able to do that quite easily.

you just need to  get the scanModem.gz into your home folder and then carry on from there.

if you have put the file on a cd-r then when you put the cd into you linux computer it should popup, then you can drag it to your home folder. (the same should happen with a floppy disk or usbstick).

if this is not happening, but it works with other cds (like the ubuntu install cd) then maybe you need to fixate/finalise the cd you burned.[/QUOTE]

Thanks again! 
got scanmodem working (took me a while to find the report file...).  It tells me it's not obvious, would need to do a lot more testing, but it thinks it (my modem) is too new and unlikely to have software support etc. - I could do more identifying and then go for "experimental" support, but I think I first of all want to get this working...  SInce it also told me that I would to re-find and install drivers with each system update, I think I'll opt for the easy way and buy a hardware modem.  I'm new to this, so why make life more complicated than need be...
Now, apart from taking every piece of paper I have about my computer to the shop, how do I go about knowing which one will work?  My guess is to start searching these forums for lists of ubuntu-compatible hardware, and then compare that list of modems with the list of modems that would work in my computer?  Anyway, that's what I'll try.  If there's anything else I need to consider please let me know!

---

### Post by Bartender on 2005-11-28
Hi, lila -
I was asking about dial-up modems last week - take a look at that thread.

[http://www.ubuntuforums.org/showthread.php?t=89861](http://www.ubuntuforums.org/showthread.php?t=89861)

Hope that helps...

---

### Post by lila on 2005-11-29
[QUOTE=Bartender]Hi, lila -
I was asking about dial-up modems last week - take a look at that thread.

[http://www.ubuntuforums.org/showthread.php?t=89861](http://www.ubuntuforums.org/showthread.php?t=89861)

Hope that helps...[/QUOTE]

Wow,
lots of info.  I have done some searching for a serial modem available in these parts (England), and I have come up with two that explicitly say they are Linux-compatible.  One costs £34, the other £117, slight difference there.  Unfortunately, on searching all the Linux forums to find if anyone had any experience with them and Ubuntu, neither comes up at all!  Does anybody have experience with a Zoom V.92 EXT 3049 external serial RS-232 Modem (the cheaper one), or with a Multitech MultiModem ZBA external serial RS-232 Modem?
Going to ask the same question to the hardware forum I think...
Thanks again, this place really is good. 
Lila

---

