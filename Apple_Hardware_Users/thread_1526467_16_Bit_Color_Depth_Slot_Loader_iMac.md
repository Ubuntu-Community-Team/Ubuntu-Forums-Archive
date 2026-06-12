---
title: "16 Bit Color Depth Slot Loader iMac"
date: 2010-07-08
forum: Apple Hardware Users
---

### Post by markosjal on 2010-07-08
I remembered that back in the old days before video cards had ridiculous amounts of memory that we used to put the color depth at 16 bits instead of 24 to get a little extra performance out of a machine.


SO I went into the xorg.conf file and found two settings Color depth and default color depth and set them both to 16 

When I rebooted there was a noticable difference in speed. I then called it a success untill the screen when WHITE when the machine was not used. It used to go black. 

I would be happy with no screen saver and the CRT instead sleeping but I can not get it to work. IN fact I have had some issues with the screen saver changing settings on its own too. 

Anyone have thoughts on this?

---

### Post by linuxopjemac on 2010-07-08
You could try with 
```
Option "DPMS"
```
in the Monitor Section

---

