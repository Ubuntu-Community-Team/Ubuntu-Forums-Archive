---
title: "how do I restore X?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by speedingbullet on 2006-11-10
I attempted to install a correct video card driver for one of my computers, but apparently I missed something, because now when I boot it up X fails to boot. Its says as part of the error log (on the input I think) fglrx says something about it not being able to recognize the chipset....


so how do I restore X to the way it was before (or at least correct the error)


thanks again....

---

### Post by r4ik on 2006-11-10
Try,

sudo dpkg-reconfigure xserver-xorg

Good luck !

---

### Post by autocrosser on 2006-11-10
After you log in (text mode)--Type:
sudo dpkg-reconfigure -phigh xserver-xorg
<return>
it will ask for your password <return>
the xorg.conf file will be reconfigured--then you can reboot or type in: <startx>

---

### Post by speedingbullet on 2006-11-10
it didnt work, its giving me a warning message : overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf .20061110013144

what should I do now?

---

### Post by rlozano on 2006-11-10
> **speedingbullet said:**
> it didnt work, its giving me a warning message : overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf .20061110013144

what should I do now?

did you continue with overwriting? just go ahead and see...

if it still fails, try removing fglrx first. i would suspect that the binary driver is not reading your new card right.

---

### Post by speedingbullet on 2006-11-10
no, it wont let me do that, it says that it would be overwriting that configuration file, and thats the reason it cant go any further...

---

### Post by taurus on 2006-11-10
Yes, you want it to overwrite the old version since the old version doesn't work!  Therefore, type exit when you see that question again...

---

### Post by speedingbullet on 2006-11-10
oh... sorry about that... most of my computer experience comes from microsoft windows, which I was using for 6 years. The only linux operating system ive ever used instead of Ubuntu was redhat 8 about 1 or two years ago... it was very confusing, and wasnt for that long either because the computer it was running on finally just died on me.


anyways my computers apperantly running ok now, thanks for the help, but I need to restart this computer just incase.

---

