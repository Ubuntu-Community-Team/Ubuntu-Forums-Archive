---
title: "HP LaserJet 1018"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by iconit on 2007-07-14
I use Ubuntu 6.10, and have an HP Laserjet 1018. I hooked up the printer via USB, and opened up the "add printer" dialague box in Ubuntu. Ubuntu identified the printer perfectly and added it.  It worked just fine for about 2 days.  Now when I try to print nothing  happens.  I can open the printer's properties dialog box and request a test page but nothing happens.   Ubuntu says it is sending it to the printer but still nothing happens.  The printer doesn't give any sign that it got any order at all. It just sits there, and doesn't print. And I know the printer is working fine because I can boot to Vista on the same PC and it works there.  I tried the suggestion offered to someone that had the same problem I do but they were using Ubuntu 7.04.  It didn't help.  I am a Newbie, help?

---

### Post by m@ra on 2007-07-14
I Noticed similar error with my Samsung ML-1510 laser... Root cause was that after standy / hibernate Ubuntu didn't detect my printer anymore. Had to now always reboot printer time after time if computer has been in energy save made.

---

### Post by jingo811 on 2007-07-14
I ran into the same problem some months ago but with my Laserjet 1020, I got a few tips but haven't had time to investigate it and test it maybe you can do some detective work on Kirk's Tech Diary.

Here's my thread:
[http://ubuntuforums.org/showthread.php?t=413002](http://ubuntuforums.org/showthread.php?t=413002)

Here's Kirk's Tech Diary:
[http://kirksblog.steffensenfamily.com/archives/13](http://kirksblog.steffensenfamily.com/archives/13)

---

### Post by GerryB on 2007-07-14
> **iconit said:**
> I use Ubuntu 6.10, and have an HP Laserjet 1018. I hooked up the printer via USB, and opened up the "add printer" dialague box in Ubuntu. Ubuntu identified the printer perfectly and added it.  It worked just fine for about 2 days.  Now when I try to print nothing  happens.  I can open the printer's properties dialog box and request a test page but nothing happens.   Ubuntu says it is sending it to the printer but still nothing happens.  The printer doesn't give any sign that it got any order at all. It just sits there, and doesn't print. And I know the printer is working fine because I can boot to Vista on the same PC and it works there.  I tried the suggestion offered to someone that had the same problem I do but they were using Ubuntu 7.04.  It didn't help.  I am a Newbie, help?

Vista is probably keeping the printer on "Ready". The easiest way to clear the buffer in a printer is to unplug it and reconnect it. You might have to do the same thing with the USB wire. Try one and/or the other. A more technically adequate answer would be appreciated from someone knowledgeable on the forum. I'm sure it's a signal by Vista. Hope it works for now.

---

### Post by Apipote on 2007-07-14
Works for me Gerry !!!
Thanks
; )

---

### Post by jingo811 on 2007-07-14
I still think that the sub link if you followed Kirk's tech diary link I gave earlier is the more descriptive solution for you 6.10 problems.

[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

---

### Post by GerryB on 2007-07-15
> **jingo811 said:**
> I still think that the sub link if you followed Kirk's tech diary link I gave earlier is the more descriptive solution for you 6.10 problems.

[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

The big question is "Why does everything work fine until the switch to Vista?" I don't have an HP printer and my Canon works fine, but I would appreciate knowing if this is the solution for people using Vista. Thank you for giving this your attention.

---

### Post by jamesford on 2007-07-16
does this work on 64 bit ubuntu too ?

---

### Post by mlyons16 on 2007-09-08
Hello,

I'm using Ubuntu 7.04 Feisty Fawn and I was using my HP LaserJet 1018 as well. I went to add printer and it detected it no problem, I used the suggested default driver, etc. etc., and it was working very nicely for my previous live cd session and now it just doesn't seem to work, since I've booted back into ubuntu using the live cd.

I'm using the Live CD still (not just yet ready to partition and install), but now, I'm having the exact same problem... no test page printing response, OpenOffice docs don't print, etc. etc.

I'll try the suggestion of unplugging it (both power and usb) to clear the print buffer from Vista (even though I'm running on a Live CD).

Any other suggestions, if that doesn't prove successful?

---

