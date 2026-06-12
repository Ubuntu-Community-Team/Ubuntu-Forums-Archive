---
title: "Can I go back to Breezy?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-08-13
I don't like what is happening to my comp now that I have upgraded to Dapper... Does anyone know what I need to do to get back to Breezy?

---

### Post by Papa-san on 2006-08-13
I searched for days to find a method to get new video drivers installed. Finally found someone who made it make sense, but the end result upon reboot is "X server disabled" or something.

I had to edit /etc/X11/xorg.conf via terminal (as well as a lot of other steps, including recompiling the kernel... I think... Maybe?!?))Now the best I get is command line only... Can't get my i dunno... like gdm or something to load...?

---

### Post by TheRingmaster on 2006-08-13
couldn't ya just use automatix or easyubuntu (both are found in the how-to section of this forum.)

---

### Post by Papa-san on 2006-08-13
I have no video driver installed. I don't know if I can use any of these things...

What would the commands be for them?

Everything was working except that I got garbage on my firefox buttons, and had occaisional system freezes that required a hard restart.

---

### Post by zxee on 2006-08-13
> **Papa-san said:**
> I searched for days to find a method to get new video drivers installed. Finally found someone who made it make sense, but the end result upon reboot is "X server disabled" or something.

I had to edit /etc/X11/xorg.conf via terminal (as well as a lot of other steps, including recompiling the kernel... I think... Maybe?!?))Now the best I get is command line only... Can't get my i dunno... like gdm or something to load...?

Have you tried > sudo dpkg-reconfigure xserver-xorg?
Make sure you know your video card specs, or at least what card you have.

---

### Post by Papa-san on 2006-08-13
Thanks!
That worked, but I still had to do a sudo aptitude update and sudo aptitude install xorg-driver-fglrx...
Then it got me back on... I don't know if this just put me back or if it fixed the freeze problem or not...

---

### Post by bonjun on 2006-08-13
-

sorry bad post... can u delete this one thanks

---

### Post by zxee on 2006-08-14
> **Papa-san said:**
> Thanks!
That worked, but I still had to do a sudo aptitude update and sudo aptitude install xorg-driver-fglrx...
Then it got me back on... I don't know if this just put me back or if it fixed the freeze problem or not...

It's good that it worked:) 
If you have freezes again look through your /var/log/xorg messages, and or start a new thread on that. Hope it's fixed for good though.

---

