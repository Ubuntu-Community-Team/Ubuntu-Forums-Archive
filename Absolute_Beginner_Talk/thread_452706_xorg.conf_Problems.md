---
title: "xorg.conf Problems"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by HenningS on 2007-05-23
Well, I just got this shiny new Dell 20" Monitor. I wanted to increase the resolution from 1280x1024 to 1440x900, which is the highest widescreen resolution my onboard graphics card can handle. I asked people on the IRC channel, they told me to add the resolution to the monitor section in xorg.conf. While I was at it, I also changed the Identifier to "Dell 2007WFP", the name of my new monitor. Now when I restarted the computer, I got this error message that told me the X server couldnt be started because of some error. Apparently, "no screens were found". So, I went into the console, edited xorg.conf, and undid all the changes I could remember making, including the resolution stuff and the monitor name. Still, the X server won't start.
Does anyone know how to fix this problem, or is there maybe a way to reset xorg.conf?

---

### Post by Seisen on 2007-05-23
To reconfigure your xorg.conf file put this in the terminal

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lazyart on 2007-05-23
```
sudo dpkg-reconfigure xserver-xorg
```

Tape it to your monitor.  You'll use it often.

---

### Post by bobplano on 2007-05-23
you could do the command 
```
sudo dpkg-reconfigure xserver-xorg
```

you should also back up any important files that your're changing. if X starts working again copy the xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
then if you ever mess it up again you can fix it easier

---

### Post by HenningS on 2007-05-23
Sounds good, I'll reboot and see what happens. Thanks!

---

### Post by HenningS on 2007-05-23
Okay, I tried it, reconfigured xorg, same problem. I think I'm just doing something wrong during the setup. Does anyone have the same monitor?

---

