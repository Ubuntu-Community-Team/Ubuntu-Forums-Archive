---
title: "Ubuntu 6.06 and 6.10 won't work on iMac G3"
date: 2007-06-06
forum: Apple PPC Users
---

### Post by blueberry17 on 2007-06-06
Hi everyone,

I have an iMac G3, and I've tried to load 6.06 on it via Live CD. The ubuntu logo shows up, and then it goes through the startup process. But then, the screen goes completely black (not even the terminal cursor is blinking), and it stays like that forever.

Any ideas how to make the graphical interface and desktop show up?

---

### Post by luckyd on 2007-06-06
Try burning an alternative install cd...

---

### Post by linear on 2007-06-07
> **blueberry17 said:**
> Any ideas how to make the graphical interface and desktop show up?

You can find the answer here: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by jazzman on 2007-06-08
Try This:


1. Boot up live CD holding down the C until the screen goes black and you hear the cd running. In your post you were having problems booting from the CD. I had a defective keyboard the first time I had this problem. Try switching keyboards if possible. (By the way, I'm using both a windows keyboard and mouse on my imac). I used a CD-RW disc that I recorded in Windows and finalized and didn't have any problems.)
2. At prompt type: live-powerpc
3. After loading everything the screen goes blank and you hear the CD running for about 2 - 3 minutes before you hear it stop,
4. Press CRTL-ALT-F1. This brings up the command line.
5. Now we need to edit the Xorg.conf file. Type: sudo nano /etc/X11/xorg.conf
6. Add a "#" at the line that says LOAD DRI. This keeps it from loading.
6a. Go to area near the bottom under "Monitor" and adjust the HorizSync to 60 and VertRefresh to75-117 respectively.
7. Go to the the area (towards the bottom of the file) where the default Depth is and change it from 24 to 16.
8. Save and exit out of nano.
9. Type: sudo killall -HUP gdm
10. This will kill and restart the GUI.
11. You will get a screen resolution of 800 x 600 with 16 color depth.

---

