---
title: "MacBook 1,1: How do I turn off the touchpad in Karmic?"
date: 2009-11-21
forum: Apple Hardware Users
---

### Post by Seamyst on 2009-11-21
For various reasons I like to use my USB mouse exclusively, and so I want to turn off the touchpad.  In Jaunty, I believe this could be accomplished by going into System >> Preferences >> Mouse>Touchpad, but now I can only disable the touchpad while typing.  Installing gpointing-device-settings doesn't work, as it says the touchpad is off, but it's not.

What do I do?

---

### Post by linuxopjemac on 2009-11-22
you can try to find out which module is responsible for the touchpad and to manually switch it off. I don't know this by know. Google a bit.

maybe this one ? [http://ubuntuforums.org/showthread.php?t=1333420](http://ubuntuforums.org/showthread.php?t=1333420)

---

### Post by Seamyst on 2009-11-22
After a bit of googling, that looks to be more complicated than I want to attempt without step-by-step instructions.  There's gotta be an easier way, too...

---

### Post by linuxopjemac on 2009-11-22
I don't know if this will work but you might give it a go:

```
sudo apt-get install gsynaptics
```

Then go to System -> Pref -> Touchpad

There is a setting to disable touchpad...this might work...I don't want to try it as I have no mouse....

---

### Post by szebacs on 2009-11-22
It seems working for me! Thx!

---

### Post by linuxopjemac on 2009-11-22
>  It seems working for me! Thx! 

I am happy that it works for you :D

---

### Post by Seamyst on 2009-11-22
Oh hey, that works!  And it's easy, too.  :)  Thanks!

Edit: It only works for about five minutes, actually, if that - then the touchpad is enabled again.  I know on earlier versions of Ubuntu editing xorg.conf would fix that, but xorg.conf doesn't seem to exist anymore (I don't think it did in Jaunty, either).  Now what?

---

### Post by linuxopjemac on 2009-11-22
ok, then we go for harder measures:
```
sudo rmmod appletouch
```

to make it work at boot you can blacklist the module in /etc/modprobe.d/blacklist.conf

just add a line in said file
```
blacklist appletouch
```

---

### Post by Seamyst on 2009-11-23
Yes, that did it!  Thanks so much!

---

