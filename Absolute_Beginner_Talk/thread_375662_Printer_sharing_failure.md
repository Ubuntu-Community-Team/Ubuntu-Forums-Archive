---
title: "Printer sharing failure"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by NevadaDave on 2007-03-04
I have Ubuntu 6.06 on my desktop, set up to boot from a separate hard drive than my XP HD. So far, I've gotten a lot of things to work (music, DVD, internet, etc.) but I am totally puzzled as to how to talk to my laptop, and share the printers on my desktop system. The desktop is connected to my 2-Wire DSL modem/wireless router via ethernet. The laptop has a wireless card to talk to the router. I have read a number of posts that discuss a variety of things to change in the cups configuration file, but so far, I cannot get the laptop to recognize that teh linux system is there. I have read a number of things about samba, but I am not sure what needs to be changed or added. I can find the IP address my system has assigend to the XP OS when it is running, but using that as suggested in other posts has not changed anything, so I'm thinking that I am missing something fundmental here. What files do I need to post to show what I have to work with so that I can make some progress? I don't necessarily really need to share files, but printing is important, because if my wife is using the laptop, she needs to be able to print. If I'm running linux, she can't (at this point, anyway).
Thanks for the help!

---

### Post by NevadaDave on 2007-03-04
Well,
I found this thread:
[http://www.ubuntuforums.org/showthread.php?t=372726&highlight=smb.conf](http://www.ubuntuforums.org/showthread.php?t=372726&highlight=smb.conf)
I used the procedure that detonate specified and... presto! I can see my Ubuntu system on my laptop, and after adding my XP HD in sahring, I can see them, also. Be sure to check the "allow browsing" buttons on the sharing setup, and be sure to stop & restart Samba after making changes.
This linux deal is starting to work out pretty good!
Thanks to all for the help!

---

