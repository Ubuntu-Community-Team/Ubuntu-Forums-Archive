---
title: "[SOLVED] slow to find USB devices"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2008-01-30
I seem to have a problem with Feisty spotting USB decices when they are plugged in.  It takes ages, in the meantime the software gives up and says no device present.

For example, I plug my camera in, F-Spot fires up and asks if I want to download pictures.  I say yes and then it tell me there is no camera present. :confused:  It must have known there was a camera present to launch itself in the first place.

Same with my printer, see previous post [here](http://ubuntuforums.org/showthread.php?t=677834)  which had zero response. :(

Typing lsusb in terminal I eventually get all my devices listed and properly identified, but it takes ages...well 2 or 3 minutes.

What gives and how do I fix it?

Thanks.

---

### Post by neurostu on 2008-02-01
First I would recommend upgrading to Gutsy, I know that Fiesty is a LTS version but in my experience Gutsy is much better then Fiesty. You also might want to try the Gutsy Live CD to see if you have the same problems.

---

### Post by Phosphoric on 2008-02-02
Hi neurostu,

thanks for the thought but I tried Gutsy once and got in to all sorts of difficulties.  Feisty was working fine  for some time, but after  unmounting a pen drive I got some sort of warning message about loosing data and I've had trouble with my USB devices ever since.

Ironically, pen drives are spotted straight away, as is my bluetooth adaptor.  My external hard drive is also OK.  It's just my printer and camera which take ages to be recognised, it's really weird.

Something must have changed and I want to change it back. :confused:

---

### Post by Phosphoric on 2008-02-02
OK tried Gutsy live CD and got the following errors when loading:

several lines of:

263.280000 usb 1-9.4: device descriptor read/64, error -110

get the same result with the live CD as I do with my Feisty install    could it be a hardware problem?

Thanks

---

### Post by jan quark on 2008-02-02
try to change in your BIOS the usb settings from 2.0 to 1.1

this might help

---

### Post by Phosphoric on 2008-02-02
> **jan quark said:**
> try to change in your BIOS the usb settings from 2.0 to 1.1

this might help

unfortunately don't have that option in the BIOS. :(

---

### Post by neurostu on 2008-02-02
Did you try running a 
```
lsusb
``` ?

---

### Post by Phosphoric on 2008-02-03
> **neurostu said:**
> Did you try running a 
```
lsusb
``` ?

Yes I've tried that, please have a look at the previous thread that I mentioned in my first post.

This is what's so weird.  The command lsusb finds all my devices and identifies them correctly.  Problem is it takes over a minute to list them.

I can't find anything about usb error code 110 that I get when installing Gutsy from the live CD.  I'm sure that should give me a clue.  I'll start another thread on that error code.

Thanks

---

### Post by Phosphoric on 2008-02-08
OK,

I'm getting seriously p****d off now.  I'm engaged in 3 different threads on this particular problem and nobody has an answer.

I'm now having serious difficulties printing,  I can wait for ages and nothing happens.  If I go in to the terminal and "lsusb" that seems eventually to spark some action and a few minutes later I'll get a document printed.  Whole process takes over 10 minutes.

Drop back in to Windows XP and everything works fine.....instantly.


Can anybody help please?  I really don't want to go back to Windows after all this time but this is  just stupid and  nobody has a solution.:(

Thanks

---

### Post by neurostu on 2008-02-08
Is there any chance you are using a usb hub?

---

### Post by Phosphoric on 2008-02-08
No USB hub,  straight from the ports connected directly from the motherboard.

I've tried different ports (4 to choose from) but to no avail. Works fine in Windows XP. :(

I have considered buying a powered USB hub but if it works OK in Windows then it can't be a hardware problem.

---

### Post by Phosphoric on 2008-02-09
Desperate bump, can't print at all now. :(

---

### Post by neurostu on 2008-02-10
Sorry man, you've reached the limits of my USB knowledge.  I wish I could help.

---

### Post by Phosphoric on 2008-02-22
Partially solved.

After more rigorous fault finding, I've traced the problem to an external hard drive that can communicate via Firewire or USB. Something has gone wrong with the USB side which is pulling the rest of my USB devices down.

So, everything is working OK now (except the USB hard drive) but I can only say that the problem is partially solved because it all works fine in Windows XP.

Yet another thing that dosen't work properly in Linux. :(

---

