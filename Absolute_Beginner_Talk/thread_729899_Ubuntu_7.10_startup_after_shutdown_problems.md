---
title: "Ubuntu 7.10 startup after shutdown problems"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by robalcorn on 2008-03-20
After powering off my system and booting up my system seems to freeze at different points when you watch the progress bar. If I hit alt f1 and watch it in verbose mode it usually boots up but sometimes freezes as different things load up like Virtualbox or gnome desktop(and yes I waited and gave it plenty of time to do whatever it was trying to do) I also have had it jump to a blank screen with a blinking cursor.If I just restart the system though there is never a problem. Any ideas as to where to look for resolution on this. Oh and the o/s was loaded about a week ago. I also looked at the system log but not sure what to look for I have seen error 15 a few days ago.

---

### Post by robalcorn on 2008-03-20
I have also tried disabling different services and sessions like "screenlets" but still no luck. The only way to get in is to power-off let it start up and freeze than hit reset button and boom system is up and running within 30 seconds????

---

### Post by spiderbatdad on 2008-03-20
it sounds like a usplash problem or possibly vga setting in the bios. 

Could you post your /etc/usplash.conf file or edit it to 1024x768?

---

### Post by robalcorn on 2008-03-20
# Usplash configuration file
xres=1280
yres=1024

I will edit to your suggestion of 1024x768 and see what happens

---

### Post by spiderbatdad on 2008-03-20
It is also common practice to run this command as well, after editing usplash, though I have never found it necessary:
```
sudo update-initramfs -u
```

---

### Post by robalcorn on 2008-03-20
No go with 1024x768 and the code you sent above either same thing. I power off and start up and system sits on progress bar for ever than locks up. Hit the reset button and system is up right away. You mentioned a setting in bios. I never changed anything there and this problem started a day or two after installing over mandriva.

---

### Post by spiderbatdad on 2008-03-20
so it sounds like a specific bios problem. you could try adding "acpi=force lapic" in place of "quiet splash" in your default kernel line in /boot/grub/menu.lst or search launchpad bugs for workarounds related to your computer make.

---

### Post by robalcorn on 2008-03-20
Well I switched quiet splash to acpi=force lapic and I tried many times shutting down and starting up but it would freeze at different points like starting gnome mgr, setting disc parameters, avahi-daemon, binfmt-support,vbox kernel..no ryme or reason to the lock up. But still boots if I hit the reset button lol. If it is a bios related problem I am tempted to reset it all but than it may create other issues as I have disabled the on board sound, ethernet and others to accomadate hardware I installed a couple of years ago in preference. I will continue to look around launchpad and hopefully something comes up from it. Well its a pain to access the system but at least I can.

---

### Post by robalcorn on 2008-03-20
Well I tried resetting the bios and disabled any on board hardware I replaced and still same problem, what doesn't make sense to me is everything is fine for a couple days and than this starts. If it is bios related I wonder if my cmos battery is getting weak but if it was I guess I would see a new system time and date as well wouldn't I. I didn't see anything on launchpad that helped either so far either. Oh well back to the drawing board.

---

