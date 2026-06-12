---
title: "i just broke my laptop :("
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-11-29
HI all, 

I was just trying to get a widescreen resolution on my nice new Compaq Presario V3118AU, and I read somewhere here on the forums that you can't achieve resolutions such as 1200x800 on the vesa driver. When i ran the reconfigure xserver-xorg, vesa was default. 

so i changed to i810 as suggested by the post, and then tried to restart xserver....

at which point it crashed... could someone tell me how I can first of all get my laptop working again, and secondly how I can achieve a decent widescreen resolution?

Thanks

Patrick

---

### Post by taurus on 2006-11-29
What graphic card do you have in your machine?

---

### Post by ozPATT on 2006-11-29
nvidia g-force go 650

---

### Post by taurus on 2006-11-29
It's an nVidia card so you can't use i815 because that driver is for Intel integrated graphic controller, those onboard graphic cards!  Try using nv when you configure X with "sudo dpkg-reconfigure xserver-xorg" command!!!

---

### Post by ozPATT on 2006-11-29
> **taurus said:**
> It's an nVidia card so you can't use i815 because that driver is for Intel integrated graphic controller, those onboard graphic cards!  Try using nv when you configure X with "sudo dpkg-reconfigure xserver-xorg" command!!!

told you i was a noob ;) 

so, is there a way to get my xserver back so i can amend the setting? or have i got to re-install everything?

---

### Post by taurus on 2006-11-29
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Now, check to see if X working or not by running "**startx**" at the prompt.  If everything is good, reboot to normal mode!

---

### Post by ozPATT on 2006-11-29
woohoo! :D all good. thanks for your help. booted in recovery, changed to nv, set the resolutions i wanted, then restarted. logged me in, and now i have widescreen and all seems to be working well! :D 

thanks a million

Patrick

---

### Post by taurus on 2006-11-29
Glad to hear it works for you.  Have fun.

---

