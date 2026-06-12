---
title: "Desktop environment wont load"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-17
I changed some values in my xorg.conf file (color depth from 24 to 32), then I restarted the computer and now the desktop environment wont load. (Black background and white text, looks similar to DOS).

How do I edit my xorg.conf file without the GUI?

Thank you :)

---

### Post by bodhi.zazen on 2006-11-17
> **PartisanEntity said:**
> I changed some values in my xorg.conf file (color depth from 24 to 32), then I restarted the computer and now the desktop environment wont load. (Black background and white text, looks similar to DOS).

How do I edit my xorg.conf file without the GUI?

Thank you :)

go ahead and log in.

```
sudo nano /etc/X11/xorg.conf
```

Always back up system configuration files before you edit them.

---

### Post by PartisanEntity on 2006-11-17
I should have backed up the file, unfortunately I did not in this case.

I did log in, but the desktop environment still does not load.

It simply remains in DOS-like appearance and appears to be a terminal.

---

### Post by bodhi.zazen on 2006-11-17
Did you type in the command I gave you:

'sudo nano /etc/X11/xorg.conf'

This will bring up an editor, nano, with xorg.conf. Edit. Ctrl-X to exit, Y to save.

Then enter "startx"

---

### Post by Blutack on 2006-11-17
Yep, you need to log in and then
if you know what you changed and remember how to change it back type 
sudo nano /etc/X11/xorg.conf
if you don't remember what you did type
sudo dpkg-reconfigure xserver-xorg
That should take you through a configuration thing - just take the defaults.
Once you have either edited th file or dpkg-reconfigured cross your fingers and type startx (NOT sudo startx!!!).  All goes well the desktop should load.  The only thing is logging out will get back to the console again - type sudo poweroff to shutdown (this is only until you reboot).
I imagine the reason it won't load is because 32 colour bits is actually 24 with something else (I vaguely remember this from somewhere) - so the highest the X-server goes is 24 bits and then does some fancy stuff to get it up to 32.

---

### Post by PartisanEntity on 2006-11-17
Ok, I did enter sudo nano /etc/x11/xorg.conf but this brought up a blank file to edit?

(sorry to pester you guys with these silly questions)

---

### Post by Abstract on 2006-11-17
> **PartisanEntity said:**
> Ok, I did enter sudo nano /etc/x11/xorg.conf but this brought up a blank file to edit?

(sorry to pester you guys with these silly questions)
You need to have a capital X. In Linux the case of filenames matters.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by TheWizzard on 2006-11-17
> **bodhi.zazen said:**
> go ahead and log in.

```
sudo nano /etc/X11/xorg.conf
```

Always back up system configuration files before you edit them.

the use 
```
sudo nano -B /etc/X11/xorg.conf
```

---

### Post by bodhi.zazen on 2006-11-17
> **TheWizzard said:**
> the use 
```
sudo nano -B /etc/X11/xorg.conf
```

Thanks for the tip. I vi most of the time now, but I advise nano because it is less threatening.

I will start using the -B flag in my advice....

---

### Post by PartisanEntity on 2006-11-17
Thanks for the help, I was able to fix the issue.

---

