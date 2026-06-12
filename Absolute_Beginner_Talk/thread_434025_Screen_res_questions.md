---
title: "Screen res questions"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by yamawho on 2007-05-05
Hi, first post here

Intalled ubuntu 7.04 on the following system;

Asus P4C800e deluxe with a P4 3.2 prescott
1 gig DDR 400 ram
Nividia FX 5200 video card
dvd-rom and floppy

I pressed f4 to set the res at 1024x768 but it didn't take on boot.
I figured I pickup the wrong one so I tried again ... same thing.
I set it up under preferences and now it's good.
Another little thing, after logging out using the live cd it tells you to remove the cd and press enter. I did and nothing happens. I have tried this cd on a few systems and this has not worked yet. I need to shut the system down by holding the start button. After it's installed it boots up and shuts down fine. I also tried enabling desktop effects. It installed the nvidia driver, I tried a few things but the window wobble was bothering me so I unabled desktop effects.

After disabling the desktop effects, I noticed the refresh rate had dropped.
I checked and it was at 53 hz when I originally set it to 85.
After checking I was still using the nvidia driver (the system loads it when you enable desktop effects) so this required me to start searching for a solution.
Didn't feel comfortable with what I was reading so I did a fresh install, much easier at this stage. So now I'm back to 1024x768 @ 85 hz.

My Viewsonic P95f supports 100hz at 1024x768.
How do I get it higher when using the nvidia driver ?

Or should I just stay with the default.

---

### Post by Happy_Man on 2007-05-05
Is it bothering you? If not, it's easier to just leave it. If you are really getting ticked off with it, run 
```
dpkg-reconfigure xserver-xorg
``` in a terminal. Go answer all the questions, remember to use the spacebar to select. Hope this helps!

---

### Post by annda on 2007-05-05
if you have the nvidia driver installed, i'd suggest using nvidia-settings - it needs to be root. if you can't find it in the menus, you can call it directly:

```
gksu nvidia-settings
```

you can also modify /etc/X11/xorg.conf manually to expand the refresh rate. but i'd go with a the nvidia tool first. and don't forget to save xorg before (back it up) and before exiting the application - there is a button.

---

### Post by yamawho on 2007-05-05
> **Happy_Man said:**
> Is it bothering you? 

Well it does when it doesn't work ...

I also found these issues;

Networking to windows systems, NAS and internet all work out of the box but I found the transfer speed on the network to be slow.
I checked and it's at 10mb/sec using e1000 driver.
I think the P4C800e deluxe uses a Marvell Yukon chip ...

Hmm ... I tried a usb key and was able to transfer stuff off it.
When it came time to remove it a right clicked on it on the desktop and there was no unmount command. So I selected eject and it disappeared from the desktop but the light on the key still remained on. I removed it later on after shutting down the system.

---

### Post by Happy_Man on 2007-05-05
If the light stays on after the icon disappears, it's ok, you can take it out no problem. It's not actually writing anything at that point, so it's perfectly safe. I have the same issue, and have never had file corruption.

---

