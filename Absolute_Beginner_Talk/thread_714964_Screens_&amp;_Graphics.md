---
title: "Screens &amp; Graphics"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by perubu on 2008-03-04
Hello there,

I run a Dell Latitude-D630 with
 a LCD Display 1440x900 @60Hz
an Adapter Type: Mobile Intel(R) 965 Express Chipset Family,

and a second Monitor Dell 1908FP(Analog) 1280x1024 @60Hz

I would like  the LCD to be the Default Screen and the external Monitor an extension, ideally to the right.

> Systems > Admnistration > Screens and Graphics       did not help: I never had two screens, at best the Monitor duplicated the Desktop LCD

running  "sudo dpkg-reconfigure xserver-org" exited with message as follows:

dexconf: error: cannot generate configuration file; 
xserver-xorg/config/monitor/horiz-sync not set.  Aborting.  Reconfigure the X 
server with "dpkg-reconfigure xserver-xorg" to correct this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration

I tried a few things in /etc/X11/xorg.conf with not success,

Reading the manual pages for xorg.conf leads me to believe there is a solution, any help is appreciated,

Perubu

---

### Post by herbster on 2008-03-04
This may help: [http://blog.dotkam.com/2007/05/18/dual-monitor-on-ubuntu-704-feisty-fawn-nc2400-with-intel-945gm/](http://blog.dotkam.com/2007/05/18/dual-monitor-on-ubuntu-704-feisty-fawn-nc2400-with-intel-945gm/)

---

### Post by perubu on 2008-04-02
I could not get it to work this way

I found xrandr that almost did the job,

Many thanks for your concern,

Père Ubu

---

### Post by Hobo Joe on 2008-04-02
Could you paste the output of:
```

glxinfo

```

---

