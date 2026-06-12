---
title: "[SOLVED] T42p Trackpoint tap to select enable"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by wahoobob on 2008-02-25
I have seen this instruction:
 "echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to _select "
and would like to know how to do this (really shy in the terminal, etc) or if there is a package to install that puts some GUI controls like (sorry) Windows.  If you can give some help here it would help me get away from XP without looking back, but now I tap my trackpoint, try to drag with the trackpoint, try to scroll with the trackpoint and get frustrated.  I guess it's the old dog new tricks thing.  
I would want this to become effective at boot and if possible, include a way to control sensitivity.  All suggestions will be appreciated.

---

### Post by Whiffle on 2008-03-01
Yep!

You'll need sysfsutils;  you can either search for it in synaptic or do
```

sudo apt-get install sysfsutils

```

Once that is installed, do;
```

gksudo gedit /etc/sysfs.conf

```

and add this line to the bottom, then save it.
```

devices/platform/i8042/serio1/serio2/press_to _select=1

```

And that should do it.

---

### Post by wahoobob on 2008-05-30
> **Whiffle said:**
> Yep!

You'll need sysfsutils;  you can either search for it in synaptic or do
```

sudo apt-get install sysfsutils

```

Once that is installed, do;
```

gksudo gedit /etc/sysfs.conf

```

and add this line to the bottom, then save it.
```

devices/platform/i8042/serio1/serio2/press_to _select=1

```

And that should do it.
Thanks for the help, I just got around to looking at the post again will try it this weekend...

---

### Post by wahoobob on 2008-05-30
works like a charm  ... thanks a million

---

