---
title: "Blurry/vibrating screen in xserver"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Pinata on 2007-11-19
Hi all,

So I installed ubuntu for the first time; installed Ubuntu 7.10 Server on my Presario 2580 laptop and then installed the ubuntu-desktop as well.  However, I cannot find the correct settings for my screen settings (at least, I'm assuming that is the problem) and whenever I 'startx', the screen is extremely blurry and shaking- basically unusable.  I have to ctrl-alt-backspace out.  I've run 'sudo dpkg-reconfigure xserver-xorg' and used the 'ati' driver, but it is still a no go.  I've tried both with HorizSync and VertRefresh set in xorg.conf, and with them unset.  However, I've not been able to find much information as to what these should generally be set to for my laptop screen.

As of now, I'm not sure how else to proceed and any help would greatly be appreciated.

---

### Post by siciliancasanova on 2007-11-19
I've had my fair share of graphics problems, especially with my ATI Radeon.  I'm no Linux master by any means, but maybe if you try using the VESA driver when you reconfigure xorg you definitely won't be operating on pristine graphics but it might be enough to gain you some functionality.

---

