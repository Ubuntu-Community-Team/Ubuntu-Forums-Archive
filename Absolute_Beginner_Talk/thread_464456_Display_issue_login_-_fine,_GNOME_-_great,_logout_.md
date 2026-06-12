---
title: "Display issue: login - fine, GNOME - great, logout - heart attack"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Dynaflow on 2007-06-04
I've returned to Linux after several years away.  I used to run Mandrake before a new job required me to work from home using a Windows machine "for security purposes" :roll: ](*,), but Debian-based Linux distros are new territory for me.  Absolute Beginner Talk seems like the place to go.

Anyway, I'm using Ubuntu 7.04, which was installed fresh over my previous, now-bulldozed Windows XP partition, and everything has been working great ... except for my ATI Radeon 9250 PCI graphics card.  I've browsed around the forums and found that this particular card and its older siblings haven't been getting along well with Feisty, but I haven't cared much because I don't game or use Beryl or any of the other semi-gratuitous eye candy programs.

On a lark, I tried to install the official ATI drivers for the card (I paid for it, so why should I have to just let it sit in my computer unused?), but the sum total of the drivers' effects on my computer was to make the display of graphics worse.  I uninstalled the drivers and have done without intense-graphics support for a couple of weeks now.

I usually shut down my computer directly from GNOME when I'm done with it (mine is the sole user account on the machine), but recently I've tried to log out and keep the computer at the login screen when unused and unattended.  Something seems to go wrong whenever I do, though.  The logout will go fine until it reaches the select-your-session-and-sign-in screen, but then the display will consistently go nuts.  It looks double-focused and fuzzy, like what you'd see if you were myopic and cockeyed.  What's going on here?  How do I figure out if this is a problem with my graphics card, xorg, or what?

---

### Post by Daishiman on 2007-06-05
Sounds like an Xorg configuration problem with the video drivers. Run a sudo dpkg-reconfigure xserver-xorg to see if that fixes anything.

---

### Post by Wim Sturkenboom on 2007-06-05
While reading some news sites, I found this: [ATI Linux x86 Display Driver 8.37.6 Released](http://www.linuxlookup.com/2007/jun/01/ati_linux_x86_display_driver_8_37_6_released)
> Logging out of a session to the graphical login manager no longer crashes the Xserver.

---

