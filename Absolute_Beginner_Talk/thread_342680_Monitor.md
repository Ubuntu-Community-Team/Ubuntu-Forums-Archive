---
title: "Monitor"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by crabhunter on 2007-01-20
I have just installed the latest ubuntu and was not happy with the monitor.
It was an old 15inch that always had a poor refresh rate.
The most ubuntu would let me set was 60.
So I robbed another system of it's 17inch IIlyama but I still am only offered a maximum refresh of 60.
The only place I've found to alter any settings is
System-Preferences-screen resolution.
I can find no mention of monitors in
System-administration-device manager
Is there somewhere else I should be loooking?
Thanks
Mike

---

### Post by pizzutz on 2007-01-20
Refresh rate settings availible through screen resolution are stored in the /etc/X11/xorg.conf  file.  you can manually change it from the terminal like this.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
gksu gedit /etc/X11/xorg.conf
```

If you are not comfortable with reconfiguring it manually, you can do it this way

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will bring up a configuration utility that will auto detect your monitor (among other things) and assist you in rewriting your config file.

---

