---
title: "Problem with resolution/refresh rate"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Ramptu on 2008-02-18
I'm having a problem with resolution and refresh rate with Ubuntu 7.10.

Here my my specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00607960&lc=en&cc=us&dlc=en&product=1843642](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00607960&lc=en&cc=us&dlc=en&product=1843642)

Monitor is Viewsonic 22" vx2235m using VGA. 1680x1050 (manual calls for 1680x1050@60Hz max)

When I goto Nvidia-settings it is showing the correct model number and resolution+refresh rate of 1680x1050@60 one one tab it shows 59.5Hz but on the main screen it is showing 60Hz. On gnome it has 3 different places where resolution can be set. Under pref>screenresolution, under admin>screen and gaphics and in the compiz settings manager.

In screen and resolution I'm showing 1680x1050 @66Hz only giving the options of 50Hz(blurry) and 66Hz clear. Under screen and graphics I'm also showing 1680x1050@66Hz. In compiz I have set it to the correct 60Hz setting. Again Nvidia-settings is showing 1680x1050@60Hz. Which one of these is reporting the correct refresh rate? I don't want to damge my monitor and Ubuntu is running great expect it completely hangs sometimes for about 5 secs. This seems independent of what is going on because I could be pushing the limits and no hang but I could be doing something less intensive and it hangs. I use the computer load monitor and my memory and cpu seem ok however when it locks up it locks up as well.

I have tried the how to guide on screen settings and added in the vert-horz rates for my monitor but it also changed my driver. After I booted I got the correct screen refresh rate but my resolution was incorrect and unable to choose 1680x1050. After getting that set in nvidia panel and correcting my driver I rebooted again and had no screen because my monitor gave the error "ut of sync range". I only got lucky and remembered the nvidia-settings entry and was able to recover, otherwise I would have had to reinstall.

I am now at 1680x1050@66Hz according to pref>screen resolution. It seems that xorg and nvidia aren't agreeing on what is to be used. Does anyone have any ideas? I new to Linux but I have googled it, the problem is some of this information you come across is outdated. Could this problem be linked with my hang-ups?


If any logs are needed or more information please let me know.

---

### Post by petersonjacob on 2008-02-18
i have noticed this too,but i would have to say that if its really not causeing a problem just leave it, my system, (outside of nvidia settings) says 50 hz, but its actually running 60, so i think its just a minor error, i would ignore it

---

