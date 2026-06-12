---
title: "PS/2 Mouse having very strange problems"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by jmetal88 on 2007-11-01
I'm using Xubuntu Gutsy and my PS/2 mouse is doing something very odd. When I first installed Ubuntu, it worked correctly all the time.  Now almost every time I start up my computer, the mouse pointer will appear, but I cannot move it or click on anything.  When this first started up, a simple warm reboot would fix the problem, but this last time I had to restart my computer five times before it would work. Also, I don't know if this was a coincidence or not, but the last two times the mouse worked on boot, I was moving the mouse around before X loaded.  I don't know if this is a bug, or if something's wrong with my configuration, or what, but I would really appreciate it if someone could help me figure out what's going wrong.

---

### Post by Partyboi2 on 2007-11-02
Have you checked /var/log/Xorg.0.log
to see if there is any errors relating to the loading of your mouse?

---

### Post by jmetal88 on 2007-11-02
I don't see any errors in xorg.0.log at all.

---

### Post by jmetal88 on 2007-11-02
Hmm... It looks like my first GRUB entry somehow got majorly screwed up. I'm not sure how, or how I would fix it, but it seems that;s the only entry that boots up with a non-working mouse. The mouse always works in Windows, and I just  booted up into this second Ubuntu entry that seems to have been created by accident sometime, and the mouse has worked every time. In the other boot entry the mouse seems to have stopped working completely (I've been restarting constantly for over half an hour now). Unfortunately, in this boot entry, my graphics are messed up and I can barely see what I'm typing right now.

---

### Post by Partyboi2 on 2007-11-02
have u tried booting into the first entry (the one without a working mouse) and In a terminal:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``````
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jmetal88 on 2007-11-02
No, I haven't tried that, but the mouse has begun working again on its own in the first entry. This is really, really random.

---

### Post by jmetal88 on 2007-11-02
Well I just tried it and my mouse stopped working. Then I rebooted and my mouse started working. I've seen other posts suggesting that this is motherboard failure, but if that were the case wouldn't the mouse sometimes not work in Windows or the other boot entries as well? 

I guess I'll find out next week when my BTX CPU cooler comes in and I can try this on my other motherboard.

---

### Post by jmetal88 on 2007-11-02
On a long shot, I just uninstalled LIRC, as it just occurred to me that my mouse didn't start having problems until I after tried to set up my Winfast TV2000 XP RM remote. I have no idea what that would have to do with my mouse, but I figured it was worth a shot. Guess I won't know for a couple more reboots though.

---

### Post by Partyboi2 on 2007-11-02
I don't think its motherboard failure, like u said it works ok in windows. You could always try changing mouse and seeing what happens.

---

### Post by jmetal88 on 2007-11-03
Well, this last time I shut down and booted up, the mouse worked the first time, so LIRC may have actually been the problem, but I guess I won't really know for a few more tries still.

---

### Post by Partyboi2 on 2007-11-03
Atleast you can see what you r typing now :lolflag:

---

### Post by jmetal88 on 2007-11-03
OK, I think I pretty much just proved that LIRC was the problem. I re-installed it and rebooted my computer, and my mouse wasn't working. Then, I uninstalled it and restarted X with Ctrl+Alt+Backspace and the mouse started working again. Why LIRC is the problem, I don't know, but it appears to be so.

---

