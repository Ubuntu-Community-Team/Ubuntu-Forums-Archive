---
title: "Screen refreshing rate PowerMacG3 / Xubuntu 6.10"
date: 2007-02-22
forum: Apple PPC Users
---

### Post by saletrk on 2007-02-22
I have installed Xubuntu 6.10 on an old PowerMac G3/300, 448Mb RAM, 20Gb HD and everything is workin OK but in Xubuntu desktop I can't get screen refreshing rate higher than 60Hz. :confused: 
Resolution is 1024x768, monitor CRT 17", graphic onboard ATI mach64 with 6 Mb video RAM.
Can anyone help with this?
I have tried with some different configurations in BootX but nothin seems to work.

Thanks

---

### Post by Asad2k5 on 2007-02-22
I have a blue white G3 400 MHZ, but could not install any linux on. Can you point me to the ISO that you have download for this G3.

I tried debian PPC and ubuntu 610 ppc  but when i boot holding the C key I got a looping message with some Default ... and nothing else.

Sorry for not offering any help for you

---

### Post by saletrk on 2007-02-22
> **Asad2k5 said:**
> I have a blue white G3 400 MHZ, but could not install any linux on. Can you point me to the ISO that you have download for this G3.

I tried debian PPC and ubuntu 610 ppc  but when i boot holding the C key I got a looping message with some Default ... and nothing else.

Sorry for not offering any help for you

I've used Alternate install CD + BootX app for OS9 with this instructions: 
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)
but I could not manage to boot in Linux after installation so I booted Mac from another SCSI disk and update driver (from OS9) on disk with Linux partition and it worked OK then.

But this screen refreshing rate is driving me crazy! Anyone?

---

### Post by jazzman on 2007-02-22
I have just loaded (2 days ago) Ubuntu 6.10 on a G3 500mhz w/384MB, slot loading. I have also loaded Xubuntu 6.10 on a G3 233mhz w/256 (Bondi Blue) using the following method.

Here were the issues I encountered:

1. I had to use a CD-R.      CD-RW, DVD-R, or DVD-RW did not work.

2. When I loaded the disk, I got the usual blank screen. This is what I did to fisx it:
a. CTRL+ALT+F1 to get to a terminal screen
b. enter:   sudo nano /etc/X11/xorg.conf
c. enter password
d. scroll to LOAD DRI and put a # in front of it. This disables DRI
e. scroll down to where you configure the screen resolution and change the HorizSync to 60.015 and the VertRefresh to 75-117
f. scroll down to DefaultDepth and change to 16.
g. CTRL X
h. Save the file.
i. enter  sudo killall -HUP gdm

This should get you back to the desktop and installation works just fine.

P.S. I had similar luck with Xubuntu 6.06 on another Bondi G3 233 with 96 mb ram. A little slow but, what the hey!

Good Luck!

Jazz

---

### Post by saletrk on 2007-02-23
> **jazzman said:**
> I have just loaded (2 days ago) Ubuntu 6.10 on a G3 500mhz w/384MB, slot loading. I have also loaded Xubuntu 6.10 on a G3 233mhz w/256 (Bondi Blue) using the following method.

Here were the issues I encountered:

1. I had to use a CD-R.      CD-RW, DVD-R, or DVD-RW did not work.

2. When I loaded the disk, I got the usual blank screen. This is what I did to fisx it:
a. CTRL+ALT+F1 to get to a terminal screen
b. enter:   sudo nano /etc/X11/xorg.conf
c. enter password
d. scroll to LOAD DRI and put a # in front of it. This disables DRI
e. scroll down to where you configure the screen resolution and change the HorizSync to 60.015 and the VertRefresh to 75-117
f. scroll down to DefaultDepth and change to 16.
g. CTRL X
h. Save the file.
i. enter  sudo killall -HUP gdm

This should get you back to the desktop and installation works just fine.

P.S. I had similar luck with Xubuntu 6.06 on another Bondi G3 233 with 96 mb ram. A little slow but, what the hey!

Good Luck!

Jazz


Thanks for help. It's much better now.

---

