---
title: "Ubuntu Server with xorg &amp; framebuffer"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by tumler on 2007-01-07
Hey, I have just installed the Ubuntu Server and I would like some help into setting up the xserver so I can use fluxbox. And if possible also the framebuffer.

I know I could use a normal ubuntu disc but I will be adding and removing apps all the time and would rather just learn how to do it myself.

Thanks in advance

---

### Post by az on 2007-01-07
sudo apt-get install x-window-system-core xterm xdm fluxbox

Forget about the framebuffer.  Everything is autoconfigured for you.

---

### Post by tumler on 2007-01-07
Thanks for replying.

I tried installing those and restarting, but when it loads up it just flashes black then fails and reverts back to command line. (I think thats xdm trying to start). 
So I login and try startx but it spits out a backtrace ending with Caught Signal 11.

---

### Post by Spano on 2007-01-07
Try it without xdm.  You may not need a display manager for what your trying to accomplish.
```
sudo apt-get --purge remove xdm
```

reboot, login, then try startx

---

### Post by tumler on 2007-01-07
No luck yet.
I tried what you said but it hasn't made any difference as to how startx responds.

BTW I forgot to mention when I run startx a few error messages popup but quickly getted pushed out of screen view, anyway to scroll up and view them?

---

### Post by Spano on 2007-01-07
scroll in terminal with 
Tab key + Page Up key 
You may need to configure your x-server
```
sudo dpkg-reconfigure xserver-xorg
```
if you don't know the answer to a prompt go with the default.

---

### Post by tumler on 2007-01-07
Finally working, Thanks alot Spano and Azz

I remember before posting I tried
```
sudo dpkg-reconfigure xserver-xorg

```

But I tried it again thanks to your suggestion and it worked.
Turns out I had to change the driver from vesa to i810

---

### Post by Spano on 2007-01-07
Excellent.

---

