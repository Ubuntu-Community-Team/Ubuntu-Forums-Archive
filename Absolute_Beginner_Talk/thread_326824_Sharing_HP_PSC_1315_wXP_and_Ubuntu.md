---
title: "Sharing HP PSC 1315 w/XP and Ubuntu"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by taylonr on 2006-12-28
Hello,

I have an HP PSC 1315 connected to my Ubuntu box.  I'd like to be able to share it with my two XP laptops.  However, I've come across some problems.

I tried doing the cups/samba combination.  I got the post script drivers from Windows/System32... location and followed the man page of cupsaddsmb.  However, I got an error every time I tried to run that.

I then tried to do IPP following this thread: [http://ubuntuforums.org/showthread.php?t=268245&page=3]("http://ubuntuforums.org/showthread.php?t=268245&page=3")

I made some progress there, the problem is when Windows asks me for a driver it does not have the PSC 1315 listed.  

I thought that was OK because I had the CD that came with the printer, but I couldn't find the driver on there.  One use suggested ENU/Drivers/WIN2k_XP but my CD (nor the install from the web) has that folder. 

All of this to say, has anyone been able to succesfully share a PSC 1315 from their Ubuntu to their XP?  If so, what driver did you use or where did you get it?

Thanks

---

### Post by taylonr on 2006-12-28
Looks like I can use the MS Publisher Imagesetter which is in the Generic section of the default XP drivers.   

If anyone is having problems with their PSC 131* printer, try that driver.

---

### Post by Pompey on 2006-12-29
Well I've got exactly the same problem but with a PSC1110. The thing is I got things working fine a few months back and I really do not understand what I am doing differently. I've spent hours trying to figure things out how I did things a few months ago, but I'm slowly coming to the conclusion it's a "Windows Update" that is screwing things up.

So for me it's working fine if already installed a few months ago, but try and make a new install and it doesn't like things unless you can find a driver that seems to work (HP suggest Deskjet 3421 as an alternative driver, but guess what? It isn't in the list of drivers and I reckon I'll only have the same problem.) ](*,)

---

### Post by Pompey on 2006-12-29
I think I've just solved the problem. It's amazing what typing a mail can do. Take a look at this: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00302767&lc=en&cc=uk&dlc=en&softwareitem=dj-7294-5&product=90787&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00302767&lc=en&cc=uk&dlc=en&softwareitem=dj-7294-5&product=90787&os=228&lang=en)

Seeing as you have a PSC 1315 I'll guess you'll also need to download the Deskjet 3420 driver like I just did and then go through what you and I have been doing for hours. I had to use the inf file I found in "win2k_xp\enu\drivers\win2k_xp"

Hope it works for you to

---

### Post by Pompey on 2006-12-29
BTW - I still can't figure out why it worked in the past. The old network definition that works clearly states that it's the psc 1110 driver that is being used when I look at the properties. Uuuummmh - Windows, I think I'll stick with Linux.

---

### Post by taylonr on 2006-12-29
Thanks for finding that.  I was going to search for compatible drivers, but then found the MS driver.  Until that breaks, I'll stick with it, rather than trying what HP suggests and hosing everything up.  Right now I have both XP machines printing fine on my Ubuntu.  

The only thing I have left is to try Ubuntu on my laptop and see if it handles my USB wireless card...

Thanks again.

---

### Post by Pompey on 2006-12-30
You could always make a second network printer install with the same information but just a different driver. Window will call it something like "printer name (copy)". I did this no problem and at least you have the comfort of knowing that HP is telling you that the DeskJet 3420 is compatible.

Also many thanks to you as I struggled for hours to find a relevant thread. I'd still like to know  why things worked without a problem using the PSC1110 driver a few months ago.

---

