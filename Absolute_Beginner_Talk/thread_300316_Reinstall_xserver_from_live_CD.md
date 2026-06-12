---
title: "Reinstall xserver from live CD"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by meshback on 2006-11-15
Is it possible to reinstall xserver from the live cd?  I was upgrading an old nvidia video card to a newer ati radeon card.  I thought that since I had the nvidia drivers installed, I should delete them before installing the ati card.  I'm assuming that in deleting the drivers, I also deleted some parts of xserver.  Now when it boot ups, it gives me the xserver failed to start message.

I've tried going to the recovery console and running the sudo dpkg-configure xserver-xorg command, including with the switches -phigh.  It comes back telling me that xserver is not installed or broken.  So from there I tried doing apt-get install xserver, but from what I can tell, my network isn't connecting so I'm not able to get the files.  

I've tried various things to get the network up, but haven't had any luck so I'm not able to get the files through apt.  Is there anyway I can repair/reinstall xserver from the live CD?  If all else fails, I'll just do a new install, but I'd prefer not to do that since I've had the system up for at least 6 months and it's always a pain trying to go back and get everything the way you had it.

Thanks for any advice!  :)

---

### Post by lazyart on 2006-11-15
sudo aptitude install unbuntu-desktop

Not detecting a network connection, it should prompt you for the cd.

---

### Post by meshback on 2006-11-16
> **lazyart said:**
> sudo aptitude install unbuntu-desktop

Not detecting a network connection, it should prompt you for the cd.

Well, unless I missed something, when I tried both the ubuntu-desktop command or xserver-xorg, it just scrolled through the list of sources, and then stopped.  It never did prompt for the CD, I had it in the drive in case it would automatically hit it.  Since I couldn't get the network up it never did  reinstall xserver.

Thanks for the help though.  I just went ahead and did a clean install, got tired of trying to puzzle this thing out.  And I figured it wouldn't hurt to clean off all the junk I've installed in the past 6 months.

---

### Post by bulldog on 2006-11-16
In the future you just install the ATI drivers,Ubuntu detects your nVidia drivers and will offer to uninstall them first.

When you uninstalled the nVidia drivers did you uninstall the restricted-modules as well?

Could be your problem.

A fresh install won't hurt,but you learn much more to try and solve the problems.

---

### Post by ironcladlad on 2007-02-05
try the following 

```
sudo apt-get install xserver-xorg
```
all that was off the top of my head so it might not work.. but its worth a try

---

### Post by GuDoN on 2008-02-21
just try reinstalling graphics drivers.

you can even try: apt-get install nvidia-glx-new

---

