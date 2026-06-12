---
title: "This is the worst trouble I have gotten in..."
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-03-04
I tried to update my i810 drivers as per this thread [http://ubuntuforums.org/showthread.php?t=364750&page=4](http://ubuntuforums.org/showthread.php?t=364750&page=4)

I know, I know it was at my own risk heh...needless to say it didn't work, and now when I try to reinstall the original i810 driver from the terminal it spits errors. -f install wants to install the old default drivers, but it runs into this:

sudo aptitude install xserver-xorg-video-i810

unpacking xserver-xorg-video i810 (from.../xserver-xorg-video-i810
_1%3a1.6.5-0ubuntu3_i386deb (--unpack) :

tryng to overwrite '/usr/lib/xorg/modules/drivers/i810
-dv.so', which is also in package xserver-xorg-video-modesetting
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
var/cache/apt/archives/xserver-xorg-video-i810_1%3a1.6.5-0ubuntu3_i386deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of xserver-xorg-video-all:
xserver-xorg-video-all depends on xserver-xorg-video-i810; however, you are screwed because xserver-xorg-video-i810 is not installed.
dpkg: error processing xserver-xorg-video-all (--configure) :
dependancy problems - leaving unconfigured
dpkg: dependancy problems prevent configuration of xserver-xorg:
xserver-xorg depends on xserver-xorg-video-all, however, you are screwed because
package xserver-xorg-video-all is not configured yet.
dpkg: error processing xserver-xorg (--configure) :
dependancy problems - leaving unconfigured
Errors were encountered while processing:
xserver-xorg-video-all  
xserver-xorg


COOL HUH....

Any ideas anybody :confused:                                              







-

---

### Post by Ripfox on 2007-03-04
I tried to update my i810 drivers as per this thread [http://ubuntuforums.org/showthread.php?t=364750&page=4](http://ubuntuforums.org/showthread.php?t=364750&page=4)

I know, I know it was at my own risk heh...needless to say it didn't work, and now when I try to reinstall the original i810 driver from the terminal it spits errors. -f install wants to install the old default drivers, but it runs into this:

sudo aptitude install xserver-xorg-video-i810

unpacking xserver-xorg-video i810 (from.../xserver-xorg-video-i810
_1%3a1.6.5-0ubuntu3_i386deb (--unpack) :

tryng to overwrite '/usr/lib/xorg/modules/drivers/i810
-dv.so', which is also in package xserver-xorg-video-modesetting
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
var/cache/apt/archives/xserver-xorg-video-i810_1%3a1.6.5-0ubuntu3_i386deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of xserver-xorg-video-all:
xserver-xorg-video-all depends on xserver-xorg-video-i810; however, you are screwed because xserver-xorg-video-i810 is not installed.
dpkg: error processing xserver-xorg-video-all (--configure) :
dependancy problems - leaving unconfigured
dpkg: dependancy problems prevent configuration of xserver-xorg:
xserver-xorg depends on xserver-xorg-video-all, however, you are screwed because
package xserver-xorg-video-all is not configured yet.
dpkg: error processing xserver-xorg (--configure) :
dependancy problems - leaving unconfigured
Errors were encountered while processing:
xserver-xorg-video-all
xserver-xorg


COOL HUH....

Any ideas anybody

---

### Post by mrmonday on 2007-03-04
Try:
```
sudo dpkg-reconfigure xserver-xorg
```
Most of the options can be left as default however make sure you choose the right driver from the list.

---

### Post by taurus on 2007-03-04
What happens if you run

```
sudo aptitude update
sudo aptitude install xserver-xorg xserver-xorg-video-all
```

---

### Post by Ripfox on 2007-03-04
dpkg-reconfigure xserver-xorg:

xserver-xoerg is broken or not fully installed

As for sudo aptitude install xserver-xorg xserver-xorg-video-all

I get the text from the first post

Thanks for the efforts here, I really dont want to lose all my stuff and reinstall....:confused:

---

### Post by Ripfox on 2007-03-04
ok, I Fixed it...whew...had to UNINSTALL the "modesetting" package, then it tried to do the same solution which ws to install the original i810 package, but I selected "no". The next solution was to remove the modesetting package, accepted it, THEN reistalled the original i810 driver....viola!!

wow...guess it is a long road, but hey, I even got Beryl workin' again! :guitar:

---

