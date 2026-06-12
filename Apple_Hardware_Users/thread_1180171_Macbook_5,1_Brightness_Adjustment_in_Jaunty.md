---
title: "Macbook 5,1 Brightness Adjustment in Jaunty"
date: 2009-06-06
forum: Apple Hardware Users
---

### Post by undoIT on 2009-06-06
It is great that both the screen brightness and keyboard backlight brightness buttons are working without any hacks in Jaunty. There are a couple issues:

1. Brightness adjustment is very slow. If I hold down the key to decrease screen brightness, it takes a long time to go from brightest to dimmest setting. Is there a way to speed this up?

2. Brightness resets after each reboot for both screen and keyboard backlight. Both are set at the brightest setting. I'd like to have the brightness settings remembered between reboots. There was a script ercoppa put together based on nvclock (see post below)

[http://ubuntuforums.org/showpost.php?p=6463978&postcount=149](http://ubuntuforums.org/showpost.php?p=6463978&postcount=149)

However, Jaunty isn't using nvclock. I have tried adjusting Power Management settings and gconf-editor, but the brightness settings still reset to max.

These are the last remaining issues for me and other than the battery life issue, my Macbook is getting near perfect :)

---

### Post by clanceyp on 2009-06-08
How did you get the screen brightness to work? When pressing F1/F2 I get the icon in the top right of the screen, but the brightness doesn't actually change : ( 

The brightness is quite low, so any help would be very much appreciated !! : )

(BTW: MacBookPro5,1 - Ubuntu 9.04)

---

### Post by cyberdork33 on 2009-06-08
> **clanceyp said:**
> How did you get the screen brightness to work? When pressing F1/F2 I get the icon in the top right of the screen, but the brightness doesn't actually change : ( 

The brightness is quite low, so any help would be very much appreciated !! : )

(BTW: MacBookPro5,1 - Ubuntu 9.04)
Please see the documentation for your mac version:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by _mario_ on 2009-06-09
> **undoIT said:**
> 
2. Brightness resets after each reboot for both screen and keyboard backlight. Both are set at the brightest setting. I'd like to have the brightness settings remembered between reboots. There was a script ercoppa put together based on nvclock (see post below)

[http://ubuntuforums.org/showpost.php?p=6463978&postcount=149](http://ubuntuforums.org/showpost.php?p=6463978&postcount=149)

However, Jaunty isn't using nvclock. I have tried adjusting Power Management settings and gconf-editor, but the brightness settings still reset to max.

besides from using suspend, you could either patch gnome-power-manager to store those values before rebooting or write a script similar to the script mentioned above that uses the driver's sysfs files instead.

ciao,
Mario

---

### Post by jacinf on 2009-07-16
Hello,

After installing all the files in the PPA for Mactel Support I can now adjust my screen brightness using F1 and F2.  For some reason after adjusting the brightness to where I want it (Full Brightness), it will adjust down to about mid-brightness after about 30 seconds or so.

Is there a config or something I can adjust or is this just the way it is?  Kind of annoying that it won't stick to the full brightness.

---

### Post by jacinf on 2009-07-16
> **jacinf said:**
> Hello,

After installing all the files in the PPA for Mactel Support I can now adjust my screen brightness using F1 and F2.  For some reason after adjusting the brightness to where I want it (Full Brightness), it will adjust down to about mid-brightness after about 30 seconds or so.

Is there a config or something I can adjust or is this just the way it is?  Kind of annoying that it won't stick to the full brightness.

Nevermind.. In the Power Management settings there is an option to dim the screen when the system is Idle.  That was selected.  Unchecking it fixed the issue.

---

### Post by brainspire on 2009-08-01
I tried this but I still have the brightness issue on my macbook pro 5.1 :(

---

### Post by brainspire on 2009-08-01
> **_mario_ said:**
> besides from using suspend, you could either patch gnome-power-manager to store those values before rebooting or write a script similar to the script mentioned above that uses the driver's sysfs files instead.

ciao,
Mario

Ok, this works after following the instructions in the link and setting the brightness to max then rebooting :-) But you can't control the brightness though the f1 and f2 keys anymore.

Thanks Mario for the direction :D

---

