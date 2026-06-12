---
title: "Software evaluation would be good."
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by SomeGayDude on 2005-09-05
We need a thread to evaluate software for the newbies (like me) and for the newbies (like me) to ask the experts (not me) for recommendations.

I've been looking for something to take to pics off my camera and save them as JPG and something like Visual Basic.  Any suggestions?

---

### Post by wmcbrine on 2005-09-05
[QUOTE=SomeGayDude]We need a thread to evaluate software for the newbies (like me) and for the newbies (like me) to ask the experts (not me) for recommendations.[/quote]I thought that was every thread? :)

> I've been looking for something to take to pics off my camera and save them as JPGMostly likely they're already in JPEG/JFIF format. If you take your camera's memory card, stick it in a card reader, and plug the reader in, you should get a folder on your desktop with the pictures. You can drag them from there (or move them from the command line). There's also an automatic photo import thing that pops up when you attach the reader, but it doesn't work for me. (I haven't spent any effort to fix it since it's so easy to grab them from the filesystem.)

Right-click on the reader's icon and unmount it before you disconnect it. 

P.S. Although I'm having a little trouble getting mine to show up right now...

> and something like Visual Basic.There's [Gambas.]("http://gambas.sourceforge.net/") If you're not set on BASIC, there are a lot of other choices.

---

### Post by davmac on 2005-09-06
I do exactly the same (mount it as an external disk and copy them to my hard disk) and then use F-Spot to organise my pictures. It is a little like Picasa and you can install it with "sudo apt-get install f-spot".

For the VB replacement, I gather that REALBasic is about as close as it gets, but you'll find more advice and info on the Programming Talk forum. [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

HTH,

Dave Mac

---

### Post by Jussi Kukkonen on 2005-09-06
[QUOTE=SomeGayDude]I've been looking for something to take to pics off my camera and save them as JPG...[/QUOTE]

Have your tried gThumb (included in the default install, I believe). Select *File/Import photos...* to get your pics off the camera.

[QUOTE=SomeGayDude]something like Visual Basic.  Any suggestions?[/QUOTE]

You were already offered some Basic-variations, but there are probably better choices for whatever you are doing. You most probably won't find the same kind of drag'n'drop development environment though, definitely not graphical GUI designers... 
 If you want scripting, take a look at shell scripting, Python, PHP, Perl or Ruby. If you're looking for good frameworks/standard libraries check out Java or C#/Mono.

---

### Post by xequence on 2005-09-06
[QUOTE=SomeGayDude]We need a thread to evaluate software for the newbies (like me) and for the newbies (like me) to ask the experts (not me) for recommendations.

I've been looking for something to take to pics off my camera and save them as JPG and something like Visual Basic.  Any suggestions?[/QUOTE]

Ive heard KBasic is like visual basic. I dont know if its KDE only though.

---

### Post by SomeGayDude on 2005-09-07
Thanks everyone.  This is so cool.  I don't have a card reader, I've always just plugged the USB into the camera.  It worked exactly the same.  The cool thing about it is that I don't need any driver for them like with winders.  And no B.S. stuff about the RAW format that needed software to convert.  Thank a million.  The only reason I was asking about VB is that I've taken in college and will have 2 more classes left.  I'm working on Network Administration.  But, I'll probably change it again.  (Changes every year).  Have fun

---

### Post by bitgroper on 2005-11-01
REALbasic is the closest to VB, and genuine X-plat, but I have no clue how to install it. I'll post when I find out how...

---

### Post by zerhacke on 2005-11-01
If your camera is relatively new, or not so relatively new, chances are it will work with Gthumb.  Even estoeric hardware is supported with it.

The thing is that many camera makers fought for quite a while to make their system the default, causing the need for special software in Windows to download the images off the camera.  After a while most everyone adopted a standard (the name of which I cannot remember right now but is essentially SCSI over USB).  If your camera uses one of the standard styles of memory stick, it's 99% probable that your camera will be supported by Linux.  If your camera is old enough or wierd enough that it required special software in Windows to import the pictures, you may be out of luck.  You may get lucky and Gthumb's import may still work, but it's a crapshoot.

Since you already said that your camera didn't need any special drivers, it's probably automagically supported by Gthumb.  Have fun with it.

Just a tip, Gthumb imports your photos to your home folder, in a folder named the date and time you imported the photos.  So if your username is johndoe and you imported them on November 1, 2005 at exactly 9 in the morning, the photos would be located at /home/johndoe/2005-11-1--09.00.00.

---

### Post by LHZ on 2005-11-01
[QUOTE=SomeGayDude]We need a thread to evaluate software for the newbies (like me) and for the newbies (like me) to ask the experts (not me) for recommendations.[/QUOTE]

Have you seen this thread? It's stickied, too.

[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

---

