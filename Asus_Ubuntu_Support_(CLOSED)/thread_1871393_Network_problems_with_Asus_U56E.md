---
title: "Network problems with Asus U56E"
date: 2011-10-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by BenLebovitz on 2011-10-28
Hi, I'm having network problems with my new Asus U56E.  

Installed 10.10, 32 bit from disc (just what I had laying around, was going to upgrade after).  Install went ok, but I can't get online.  LAN and wireless works ok in windows on the machine.

I ran a systems test.  Network_test = passed, Internet_test = Failed.

Any advice what I can try next would be great.

thanks,
Ben

---

### Post by GreenRaccoon on 2011-10-30
You could try installing a newer kernel.  I have an ASUS K53E and wireless didn't even work with the 2.6.35 kernel in 10.10.  The 2.6.38 kernel in 11.04 Natty Narwhal enabled wireless, but it still had a couple of driver bugs.  My volume adjusting keys didn't work in that kernel.  The 3.0 kernel in 11.10 Oneiric Ocelot is perfect for my laptop.

The only trouble is that you'd most likely need to be connected to the Internet to install the packages (the .deb ones at least).  I personally do not know how to do it another way.  Do wired connections work for your computer?

---

