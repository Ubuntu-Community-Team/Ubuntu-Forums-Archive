---
title: "Anyone up to a challenge in setting up a broadcom wireless card?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-10-31
OK, I am about to pull my hair out.  I have tried everything that I can think of, and am at my end here... I need to get this card working in my laptop.  Anyone wanna pm or IM and help me get this going.  I have tried all the fixes I could find.  But I am a linux noob, so I could have easily done something wrong.  ANyways... let roll!  Someone pm me or post here and we can set it up!

---

### Post by ewl1217 on 2006-10-31
Have you tried using ndiswrapper? I'll try to find a guide for it real quick...

**EDIT:** Try [this guide]("http://ubuntuforums.org/showthread.php?t=25683"). If that doesn't help, try tdoing a little looking around in the [FAQs, HowTos, Tips, and Tricks Forum]("http://ubuntuforums.org/forumdisplay.php?f=100").

---

### Post by chuckyp on 2006-10-31
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I do know that you will have to blacklist the broadcomm driver installed by ubuntu and install your own with ndiswrapper.  Might I also suggest installing ndisgtk for a nice gui way of installing your windows drivers.

---

### Post by PriceChild on 2006-10-31
Try Dapper... i bet you'll get much better luck :D

Oh and i've heard of a few users who kept broadcom support after upgrade to Edgy from Dapper.

---

### Post by pastorjay on 2006-10-31
I did try Dapper, and I was unable to get it working in that either.  It may just be my noob experience with linux

---

### Post by ishift on 2006-10-31
well, i have a broadcom 4306 (belkin 54g) and, yes, i had to go through 2 heads full of hair to get it running (the other being my linux genius of a friend).

for me, i tried ndiswrapper (including ndiswrapper-utils) and ndisgtk, but the neither did the light come on nor did the card work. however, the system recognized the card.

so, after a lot of downloading (from another computer), transferring, and installing ndiswrapper packages (and some kernel images), ndiswrapper-utils 1.8 worked like a charm.

here's the thread i started:

[http://ubuntuforums.org/showthread.php?t=288514](http://ubuntuforums.org/showthread.php?t=288514)

and here's the instructions i used:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

it's pretty straightforward. as a beginner, i think ndisgtk is the easiest way. however, i was able to get it to work without it.

hope that helps :)

---

### Post by pastorjay on 2006-10-31
We have success!  I could have had a connection many times, and would have never known it until I read that the wired and wireless cannot be connected at the same time.  I know, that sounds dumb, but it has never been an issue in windows!  

Thanks for everyone's help!  I am becoming hooked on linux here!  Now, to find out why my internet hesitates everytime I go to a new site, but once connected, it flies!

---

### Post by TheMatt on 2006-10-31
> **pastorjay said:**
> We have success!  I could have had a connection many times, and would have never known it until I read that the wired and wireless cannot be connected at the same time.  I know, that sounds dumb, but it has never been an issue in windows!  

Thanks for everyone's help!  I am becoming hooked on linux here!  Now, to find out why my internet hesitates everytime I go to a new site, but once connected, it flies!
I was in the same situation with my Broadcom 4318. I eventually got it to work.

I noticed that Konqueror, it did the thing you were discribing, but firefox didn't. Now Konqueror doesn't do it either. Perhaps you should try another browser.

---

### Post by pastorjay on 2006-10-31
Well, it is not the browser itself.  I had this laptop hooked up to my network at work, and it was fine there.  It must have something to do with the settings of my router...  funny thing is, bother routers I have used are Linksys...

---

