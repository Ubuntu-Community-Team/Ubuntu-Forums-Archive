---
title: "Blank screen after live CD boot 6.06"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by TheSubtleKnife on 2008-06-13
I am trying to boot 6.06 off of the live CD, and the splash screen comes up, and everything loads fine, and when it tries to go into the GUI (gnome) the screen just turns black, but I can hear the login noise that nautilus makes when you login. Is there any way to go into safe graphics mode, or any other way to configure the display driver?
iMac G3
400Mhz CPU, 768MB ram and a Rage 128 pro

Thanks in advance,
TheSubtleKnife

---

### Post by cyberdork33 on 2008-06-13
why are you using 6.06?

---

### Post by TheSubtleKnife on 2008-06-13
because I got a ton of ubuntu CD's in the mail a while ago, and they included PPC mac disks too. and the fact that downloading a new distr takes too long over my internet...so is there any fix?

---

### Post by influx.ca on 2008-06-13
did you try 

```

live video=ofonly
```


at the boot prompt?

I had the same problem when booting off the Live CD on my iBook G4 and this was the solution.

---

### Post by influx.ca on 2008-06-13
...

---

### Post by TheSubtleKnife on 2008-06-14
well, now i get a message saying "Failed to start the X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?"
When I select yes, it just gives me a shell prompt ubuntu@ubuntu:

---

### Post by ibrastix on 2008-06-14
after it fails to load your X server, are you in a terminal or not?
if yes, ignore the next paragraph.

if not type Ctrl+Alt+F1 or F2 ...... till F6  (all of them will work), you'll find a terminal,
note that if you are on a laptop, u might have to type Ctrl+Alt+Fn+F1
Fn is the function key. 

log on using the user name and password created during the setup, then type

sudo dpkg-reconfigure xserver-xorg

it'll reconfigure you xorg.conf file.
when it comes to choosing your video driver, choose vesa. then reboot.

after you have a user interface, if you are unsatisfied with your graphics, you can install a driver that corresponds to your VGA card. guides on how to install video drivers are all over the forums.

hope i helped.

---

