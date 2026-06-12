---
title: "Need help with ZD1211 and ibook"
date: 2007-03-23
forum: Apple PPC Users
---

### Post by jomny on 2007-03-23
Ive been having a lot of trouble getting my ibook online wirelessly, and although I have reached a point where I have a semi working driver running, Im not having packets go through successfully. I really don't know what to do and my thread over in networking isn't getting me any help any more, so I turn to you fellow powerpc ubuntu users for help. Here is the thread I posted that shows the progress I have made and where Im stuck right now: 

[http://ubuntuforums.org/showthread.php?t=386278](http://ubuntuforums.org/showthread.php?t=386278)

PLEASE HELP.

---

### Post by Peter76 on 2007-03-23
Hi, just had a quick read through your other thread; in the last output you give from iwconfig it says it doesn's associate with your access point; can you set this by hand using:

sudo iwconfig wlan0 ap 00:11:22:AA:BB:CC

where the 00:11 stuf is the MAC address of your router.
Then check with dmesg if it associates with your accesspoint...

Might help..... Good luck...
Otherwise buy a 3com officeconnect usb stick; works fine on my iBook with the zd1211 driver, although I had to compile it...

---

