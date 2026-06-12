---
title: "/X11/xorg.conf"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by ChiaroScuro on 2006-12-08
Ok, I got myself into some trouble. After I had the xorg.conf set up, everything was good. I kept trying to alter it because beryl wouldn't run properly. Now since beryl wasn't running because no XGL was found (even though installed) i tried resetting my xorg.conf back to default, and it worked. The only thing is i was back to the:
Xlib: extension "GLX" missing on display ":0.0".

so i tried to modify it again!

well this time i screwed up and placed things in the wrong spot and had no x server after reboot!
i finally altered what i messed up with nano -w
and ran the sudo dpkg-reconfigure -phigh xserver-xorg .

I am back up with my x server and back to square one with my glx rendering...:D 

I also went to check my files in /X11 and i have multiple back-up of the xorg.conf](*,) 

any idea how i can fix alll this

I need to know how to erase all the xorg.conf i altered, and more importantely set up a properly working x config that again display glx rendering, and runs beryl with no xlg gripes!!!

Thanks

---

### Post by Forceflow on 2006-12-08
Boot in recovery mode and execute:
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bodhi.zazen on 2006-12-08
> **ChiaroScuro said:**
> 
I also went to check my files in /X11 and i have multiple back-up of the xorg.conf](*,) 

any idea how i can fix alll this

to see you files:```
gksudo nautilus /etc/X11
```

Delete any un-necessary backups (keep only a working copy of xorg.conf).

To back up from the CLI:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You can (and should) change the last .bak to any descriptiion to be more helpful like "xorg.cong.bak_beryl" or what have you.

---

