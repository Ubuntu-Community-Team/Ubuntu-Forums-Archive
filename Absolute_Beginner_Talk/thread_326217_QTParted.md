---
title: "QTParted"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by andrewlondonuk on 2006-12-27
I'm trying to get my hard disk set up correctly and am struggling with qtparted. I'm starting it from the command line so that i'm using root but it's only loading my disk in readonly mode.... 

I've removed my old windows partition and want to add the free space to my linux partition.... I guess this is possible but how on earth do i get qtparted to allow me to do this?

Thanks,
Andrew

---

### Post by bodhi.zazen on 2006-12-27
You can only add free space at the end of a partition. I assume your windows partition was first (in front of) your Ubuntu partition.

You can either move then resize or format the free space as ext3 (or what have you)  and mount it as a data partition.

HTH

---

### Post by Bartender on 2006-12-27
andrew - 
Is your heart set on QParted instead of GParted?  

I put together a guide for creating partitions for an all-Linux dual boot, and want to share it with you guys.  Here's a link to it, post #9

[http://www.techsupportforum.com/alternative-computing/linux-support/131773-dual-linux-os.html](http://www.techsupportforum.com/alternative-computing/linux-support/131773-dual-linux-os.html)

---

### Post by andrewlondonuk on 2006-12-27
I downloaded the gnome partition editor boot disc in the end. It is brilliant....

Download it from here...

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Thanks for the help guys.

**Update** For this to work the way i used it you will need to download the live cd iso image. Burn it to disc and boot off of that.

---

### Post by Bartender on 2006-12-27
Glad to hear you got it sorted out!

---

### Post by Incompetnce on 2007-02-21
When I open Qparted it tells me "no device found, maybe youre not using root user?" how do i get round this? basically i want to split the partition I installed linux on into 2; one for the OS, one for data. is the best way to do this via Qparted or to go onto windows (i have dual boot for now) and download partition magic on there?

---

### Post by geezerone on 2007-02-21
Did you boot into Qparted and have you selected the appropriate device which is normally shown on top RHS in Gparted?

---

### Post by bodhi.zazen on 2007-02-21
> **Incompetnce said:**
> When I open Qparted it tells me "no device found, maybe youre not using root user?" how do i get round this? basically i want to split the partition I installed linux on into 2; one for the OS, one for data. is the best way to do this via Qparted or to go onto windows (i have dual boot for now) and download partition magic on there?

IMO best way is with gparted. Some of those windows programs may not be fully compatible with linux ;)

To run gparted as root :

1. Open a terminal. Enter:
```
gksudo gparted
```

2. Download the gparted cd. Has some additional tools, well worth the download ;)

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

