---
title: "Second log in and seem stuck in loop"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by simonfoley on 2007-02-06
I managed to log in and start setting things up and then left Ubuntu for a while.  I came back to it now and only managed to get to the log in screen.  I had kind of forgotten my username (but not my password).  I tried everything I know and was getting nowhere.  However, my desktop is called simon-desktop so I figured it was 'simon'.  I tried this with my normal password and it looks like it will log on.  The timer comes up for one moment, the screen goes blank and then we return to the log in page again. 

Any ideas?

Do I need to reinstall?

S

---

### Post by Greykrrr on 2007-02-06
This sounds more like a problem with x. Have you tried to install compiz/xgl or similar software which changes the x configuration file?

---

### Post by simonfoley on 2007-02-07
Hmmm, I have installed nothing.  I did check that I have the correct log in name and this is the case.  I can not do anything else now as I can not get in

Is there a command I can enter to run normal Ubuntu from safemode?

As I have nothing to lose, is it worth going for a reinstall?

S

---

### Post by Greykrrr on 2007-02-07
Well, I cannot guarentee that this will work but you can try and reconfigure first gdm, and login again, and if that's no good reset the x-server. You do it with these commands

for gdm
dpkg-reconfigure gdm

for x
dpkg-reconfigure xserver-xorg

You may need to run these commands with sudo.

Also you can always get to a terminal by pressing <Control><Alt>F5 and switch back again by <Control><Alt>F7.

---

