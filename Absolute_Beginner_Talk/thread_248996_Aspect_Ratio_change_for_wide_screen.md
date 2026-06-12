---
title: "Aspect Ratio change for wide screen"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-01
Hi, Guys!
I'm a newbie to Linux, but have some past experience in Windows.
I had no problem in installing Ubuntu, with it recognising my hardware OK.
However, my Acer TravelMate 4101nWNLCi has a widescreen and uses the Intel 915 graphic chipset. Under Windiws I operated it in 1280 X 800 mode, giving the correct aspect ratio.
As I use CAD software often, I like circles to appear round, not as ovals.

I did the following:

**Downloaded**
sudo apt-get install 915resolution

**Ran**
915resolution -l

**I then chose the 640 X 480 resolution to modify**
915resolution 50 1280 800

What happened next was that the screen resolution did change, but I ended up with an active screen occupying the top left quarter of my display and the rest was blank.

I wasn't sure whether all that was required was a re-start, but I backed-out at this point and thought that I'd better get some help.

Any ideas?

Regards,
Roger :D

---

### Post by Shay Stephens on 2006-09-01
My laptop has a 1280x800 widescreen.  The bootup does not display right, but when I get to the login screen it does work.  To get to that point, I had to add 1280x800 to the xorg.conf file.

I have never tried the program you mentioned.

---

