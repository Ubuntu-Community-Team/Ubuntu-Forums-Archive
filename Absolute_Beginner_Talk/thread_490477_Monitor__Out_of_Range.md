---
title: "Monitor : Out of Range"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-02
I'm trying to install Ubuntu on my computer but when I run either the liveCD or the install CD it gets to a certain stage (after its got the ubuntu name on the screen and its going through things and it says either ok or failed..... don't really know how to describe it sorry) and then my monitor goes black and says "Out of Range"

My monitor is a TV enabled monitor
on windows the resoloution is 1024 x 786
32 bit color
refresh rate 60 hertz (capable of up to 75)

I had a look on google and it suggested switching (Ctrl + Alt + F*) and then typing in 
"sudo dpkg-reconfigure xserver-xorg"
and I went through that and restarted and still had the same problem

Please Help! Really want/need to install Ubuntu! :(

---

### Post by avik on 2007-07-02
> 
I had a look on google and it suggested switching (Ctrl + Alt + F*) and then typing in
"sudo dpkg-reconfigure xserver-xorg"
and I went through that and restarted and still had the same problem


And you shouldn't restart.  The LiveCD won't save its settings after rebooting.  Just go through that command and then type:

```
sudo /etc/init.d/gdm restart
```

If that doesn't work, try safe graphics mode.  And there's always the alternate CD.

---

### Post by alienexplorers on 2007-07-02
You could try a modeline in your "monitor" section of your xorg.conf file.
A modeline for 1024x768@60 would be:
> Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

Other modelines can be generated at:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by tartarian on 2007-07-02
How do I boot into graphics safe mode?
When I type in that commant I get the error "Failed to start the X server. It is likley that it is not set up correctly. 
Hmmmm alternate cd?

Thankyou!!!!!

---

### Post by avik on 2007-07-02
> **tartarian said:**
> When I type in that commant I get the error "Failed to start the X server. It is likley that it is not set up correctly. 

You typed in both commands, right?

> How do I boot into graphics safe mode?

It's an option in menu you get when you first boot up the Live CD.

> Hmmmm alternate cd?

Just download and burn the Alternate CD instead of the Live CD.

---

