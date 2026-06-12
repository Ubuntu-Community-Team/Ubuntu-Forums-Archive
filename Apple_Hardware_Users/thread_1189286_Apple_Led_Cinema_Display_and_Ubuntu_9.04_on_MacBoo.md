---
title: "Apple Led Cinema Display and Ubuntu 9.04 on MacBook Pro not working"
date: 2009-06-16
forum: Apple Hardware Users
---

### Post by sagilca on 2009-06-16
Hi,

I've just installed Ubuntu 9.04 on a MacbookPro (5.1) and everything is almost working now (my wifi connection seems to work a little randomly), except for the external monitor, an Apple 24" led cinema display. When I try to configure it, both as twinview and as standalone monitor, I only get a green weird image, as if the frequency was wrong or something. (I've checked it and it's 60 hz, what I am using). I was using the nvidia driver 180 but I tried too removing this driver and similar results. 

I've been searching info, but nothing I've found has been helpful.

Any ideas?

Thanks.

---

### Post by hajk on 2009-06-23
Even the latest "nvidia" Linux drivers won't work through the mini display port, but the simpler "vesa" driver does (simpler in the sense that there is no 3D). To get to the full 1920x1200 resolution you must give Xorg a hand:

In the Section "Monitor" add something like:```

       HorizSync    69.0 - 79.0
       VertRefresh  55.0 - 65.0
       Modeline     "1920x1200" 204.95 1920 2024 2272 2744 
                                       1200 1200 1203 1244
```and in the Section "Screen" add:```

       DefaultDepth 24
       SubSection   "Display"
                    ViewPort  0 0
                    Virtual   1920 1200
                    Modes     "1920x1200"
       EndSubSection
```
These settings work for me, but it is a bummer that "vesa" doesn't support accellerated garphics...

---

### Post by sagilca on 2009-10-20
Hi, Hajk.

Thanks for the reply. I've just tried these settings and it doensn't work for me. My problem is that the LED display is not detected unless I am using the last version of NVidia drivers. Using VESA it's not detected. I tried to boot from a live CD with the last Ubuntu (beta) version and I have the same problem. 

Any ideas?

Thanks,

Sara

---

### Post by hajk on 2009-10-21
Sorry, the problem is the implementation by Apple of the (mini) display port. The latest nvidia module for the Linux kernel results in a tangle of green and yellow lines on the screen, perhaps a timing issue. There is no such problem when hooking up to another LCD screen using the MDP-to-DVI adapter. 

Curious that the vesa driver doesn't work for you, it should give you at least some resolution (like 800x600) even without an /etc/X11/xorg.conf file present. It does so both when using the Apple 24" LED Cinema Display through the mini display port on a recent Mac Mini and on a MacBook Pro 13", in both cases with the Ubuntu 9.04 Jaunty liveCD. 

Meanwhile, I've gotten tired of these problems and have switched to running Linux on my Macs in a Parallels VM (VMware Fusion or even the free VirtualBox would also work).

---

### Post by proycon on 2009-10-21
Unfortunately there seems to be no solution to this yet, or rather, there is a fix but nvidia has not released it yet. It will be available in the 195.* driver. See the thread I started on the nvidia forum for details: [http://www.nvnews.net/vbulletin/showthread.php?p=2106289](http://www.nvnews.net/vbulletin/showthread.php?p=2106289)

---

### Post by tigrux on 2009-11-25
Nvidia driver 195.xx are on the wild!
Get them from the nvidia site (in the section of beta and archived).

The Led Cinema Display works fine with karmic and that version.

---

### Post by linuxopjemac on 2009-11-26
good news :P

---

