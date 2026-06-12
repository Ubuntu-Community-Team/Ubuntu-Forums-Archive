---
title: "X server Keyboard vs Gnome Setting"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-10-23
I receive the following message after I uninstalled compiz and xserver-xgl from my laptop.

```
The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc104", layout "us" and no options.

Which set would you like to use?
```

I have checked the xorg.conf and also the system preference for my keyboard and both are pc104.

I have even tried to use sudo dpkg-reconfigure xserver-xorg to reconfigure the set-up but still the message box pops up.

Any help?

Thanks

---

### Post by dca on 2007-10-23
What's listed under System -> Preferences -> Keyboard -> Layouts Tab Option?

---

### Post by in_flu_ence on 2007-10-23
Generic 104-key PC U.S. English

I am using a compaq presairo V2000 series laptop just in case.

---

### Post by OldGrey on 2007-10-23
I am having a similar problem:

[http://ubuntuforums.org/showthread.php?t=587109](http://ubuntuforums.org/showthread.php?t=587109)

Though I want a UK configured keyboard.

---

### Post by dogskull on 2007-10-24
Solution on the other thread: [http://ubuntuforums.org/showpost.php?p=3625494&postcount=5](http://ubuntuforums.org/showpost.php?p=3625494&postcount=5)

---

### Post by dsfitzpat on 2008-02-11
Hi, I also had this problem, and seem to have corrected it with a pretty straight-forward fix:
Under System --> Preferences --> Keyboard  click on the Layouts tab.
The only layout I have listed is US English, but the Default radio button next to it was unchecked.
Clicking on the button seems to have taken care of it.

---

