---
title: "LIVE CD Permissions"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by RAH66 on 2007-06-21
Well I just got Ubuntu Feisty 7.04.

I did some research so I could be prepared for the installation and driver setup etc... 

Well looks like I didnt do enough everything went great with the installation I followed tips like to do it in safe graphics mode and get your drivers while using live cd it all went fine but when I restarted my pc the loading screen comes up and then after it loads I get an OUT OF RANGE msg on my screen 
( BENQ FP92W 19" Wide screen) ( Nvidia GeForce 6600 GT )

I then booted windows again to expand my knowledge of ubuntu further...
found out you have to sudo dpkg-reconfigure xserver-xorg I had to do this through the recovery console or with ctr + alt + F2 well didnt work couldn't fix screen out of range issue I did this hundreds of times testing all the common refresh rates and res's sometimes i get funny errors or just the out of range.

Well as a last effort I want to Boot the Live cd mount the drive ubuntu is on and then edit the xorg.conf file 
and then save it but I dont seem to be able to have permissin to do so when using Live mode.

(other than that im gona have to dump ubuntu or my screen :| )

I love what I have seen ubuntu can do so I'm not ready to give up yet any help is welcome thanx

---

### Post by atria on 2007-06-21
Try booting with the second option (Safe mode)

If you want to edit xorg.conf, make sure that your editor has root privileges.

In case you're using nano,
```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by RAH66 on 2007-06-21
I have a copy of xorg.conf that I saved on my flash drive that I've edited so i actually just want to copy over the one on the disk that i have mounted 

yeah thats the problem I dont know how to get those privilages

---

