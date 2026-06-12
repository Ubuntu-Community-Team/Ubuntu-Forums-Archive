---
title: "xorg.conf error"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-05-09
I was trying to follow [this](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon) guide to install beryl.  But when I got to the point where I was supposed to restart X by pressing Ctrl-Alt-Backspace, my computer restarted and I got the error:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem

<Yes> <No>

When I hit <Yes> I get:

Fatal server error:
no screens found

Then I ht <Ok> and I get:

The X server is now disabled.  Restart GDM when it is configured correctly.

Then it takes me to a command line interface.

Can anyone help me out?  I just want to get my computer back to how it was before.

---

### Post by Seisen on 2007-05-09
```
sudo dpkg -reconfigure xserver-xorg
``` in the terminal.

---

### Post by Brucey on 2007-05-09
When I type that in this is what I get:

dpkg: conflicting actions -e (--control) and -r (--remove)

and then a list of commands.

What do I do now?

---

### Post by Seisen on 2007-05-09
Im stupid here is how its supposed to look

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by MOS95B on 2007-05-10
Thank You!!!

---

