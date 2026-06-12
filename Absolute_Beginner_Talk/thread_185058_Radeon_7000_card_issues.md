---
title: "Radeon 7000 card issues"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Ken Burgard on 2006-05-31
I presume that my sys has video card issues.  Running 5.10 with a Radeon 7000 video card, the monitor will black out and display "video mode not supported", when I try to run TUX and Gcompris  applications.  Takes luck to pull it out of the abyss without power down. Native resolution of 1600 x 1200 AND 800 x 600 is enabled.

I see on the ATi driver site, my card is linux supported.  It is most unclear what I need to do though.  How do I see what driver is currently installed?  

Also, I found drivers and saw a "Driver Installer" available through the ATI site.  The installer was 70 MEGS! WHAT! Could this be right? 

My monitor is a Samsung SyncMaster 213T, LCD. It all works fine in Windows ME.

---

### Post by deja2004 on 2006-05-31
Follow the directions on the site. I have an ATI x600 (on my laptop) and it worked out great. Let me know how it goes!

---

### Post by linbetwin on 2006-05-31
[quote=Ken Burgard]I presume that my sys has video card issues.  Running 5.10 with a Radeon 7000 video card, the monitor will black out and display "video mode not supported", when I try to run TUX and Gcompris  applications.  Takes luck to pull it out of the abyss without power down. Native resolution of 1600 x 1200 AND 800 x 600 is enabled.

I see on the ATi driver site, my card is linux supported.  It is most unclear what I need to do though.  How do I see what driver is currently installed?  

Also, I found drivers and saw a "Driver Installer" available through the ATI site.  The installer was 70 MEGS! WHAT! Could this be right? 

My monitor is a Samsung SyncMaster 213T, LCD. It all works fine in Windows ME.[/quote]

You don't need the ATI proprietary drivers for a RADEON 7000 card.

If you haven't fiddled with the file /etc/X11/xorg.conf, you are probably using the "ati" driver. You can replace that with the "radeon" driver, which offers better performance. search for "radeon 7000" on these forums or on google, and you will find how to configure xorg.conf with the "radeon" driver and extra options.

---

### Post by Ken Burgard on 2006-06-03
PROBLEM SOLVED!

The best things in life are simple and free.  This was, in the end, not a video card issue, I think.  By researching, then entering in xorg.conf, the Horizontal and Vertical sync rates for my monitor, a SnycMaster 213T, all now works.

Thank you all for your assistance.

---

