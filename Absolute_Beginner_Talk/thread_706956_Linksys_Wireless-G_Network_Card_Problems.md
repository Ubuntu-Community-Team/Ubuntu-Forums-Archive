---
title: "Linksys Wireless-G Network Card Problems"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by matherians2 on 2008-02-24
Hello folks,

I just recently converted from Windows XP to Ubuntu Linux.  I am trying to get my Linksys Compact Wireless-G network adapter to work.  The model number is WUSB54GSC.  I have seen previous posts and it seems a bit too complicated for me.  So far, I added the NDISWrapper application, but can't get it to work.  Also, I have a Pentium 4 processor.  Somebody please help me, and please explain it in New User terms.

---

### Post by achianese on 2008-02-24
Have you seen this?

[http://www.paulie-pages.com/?tag=gutsy](http://www.paulie-pages.com/?tag=gutsy)

---

### Post by Hospadar on 2008-02-24
Hi!
I think I might have the same card, I believe it has a ralink rt73 chipset.

could you try posting the output of "lsmod |grep 73" and "lsmod | grep rt"

If it's the card I think it is I've used [this]("http://ubuntuforums.org/showthread.php?t=400236") guide to setup that hardware successfully before.  It will require you to configure the card manually, and I've never gotten mine working with WPA, but with WEP and no-encryption networks it works like a dream (manual configuration isn't a biggie once you learn how to do it)

If you have the card I have, this will work a lot better than ndiswrapper (if you don't need wpa and can survive some trivial hand-config)

---

### Post by matherians2 on 2008-02-27
Through NDISWRAPPER, it doesn't work.  I think I will wait for the upgraded version to come up with a better package.

---

### Post by myddewji13 on 2008-02-28
this is a shot in the dark but try using this thread to enable ndiswrapper.... 
[http://ubuntuforums.org/showthread.php?t=709447](http://ubuntuforums.org/showthread.php?t=709447)

---

### Post by ushills on 2008-02-28
I had this card and no amount of configuration would get it to work with WPA, changed it for a RT61/RT2561 and although it didn't work out of the box it works very reliably and I now use this card in all 3 machines.

---

