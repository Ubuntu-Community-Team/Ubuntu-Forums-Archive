---
title: "Help! Changed ati graphics card now only boots to console"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by yxxxx on 2007-10-18
Hello i need some help.

I recently replaced my old ati radeon x600 pro graphics card with a radeon X1950 Pro and now it will only boot to console.

Now im very new at all this and have been looking all over the place for solutions and as yet havent found one that will work.

I have tried reconfiguring the xorg thing multiple times with out success and frankly now im out of ideas
so any help would be greatly appreciated. 



Processor:  	
Intel(R) Pentium(R) 4 CPU 3.40GHz 

Memory:1024MB ddr RAM

Video Card: 	
Radeon X1950 Pro

have beryl installed amounst others

---

### Post by NilsE on 2007-10-18
Try going in the etc/X11/ folder and remove the xorg.conf file and reboot.  This will let it rebuild the config for the new display.

---

### Post by skymera on 2007-10-18
ok im guessing driver error

do this:

sudo dpkg-reconfigure xserver-xorg

then get envy, run the scriupt and your driver worries are over! :D

---

### Post by twiceasworn on 2007-10-18
I would hazard a guess that you were using the open source driver and I am pretty sure the newer and better ati cards aren't working with it.  Either way, just reconfigure xorg and choose the vesa driver when it asks.  This is a terrible driver but it will get you back to a desktop and give you the ability to install fglrx or whatever else you need.
```

sudo dpkg-reconfigure xserver-xorg
```

Really the only thing you should concern yourself with when you run that program is the driver and monitor settings, everything else you can just hit enter to get past as it is all most likely correct.

Also, word of wisdom:  The next time you buy a graphics card, go with Nvidia, MUCH better support.

---

### Post by yxxxx on 2007-10-18
> **twiceasworn said:**
> I would hazard a guess that you were using the open source driver and I am pretty sure the newer and better ati cards aren't working with it.  Either way, just reconfigure xorg and choose the vesa driver when it asks.  This is a terrible driver but it will get you back to a desktop and give you the ability to install fglrx or whatever else you need.
```

sudo dpkg-reconfigure xserver-xorg
```

Really the only thing you should concern yourself with when you run that program is the driver and monitor settings, everything else you can just hit enter to get past as it is all most likely correct.

Also, word of wisdom:  The next time you buy a graphics card, go with Nvidia, MUCH better support.


Thank you very much that worked. I had tried that command before but had always gone for the ati driver.

Thanks everyone for your reply's.

---

