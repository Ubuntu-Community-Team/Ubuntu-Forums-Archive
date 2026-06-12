---
title: "MacBook Pro Smoking Hot!!!!"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-06
Well it is not really smoking but it gets damn hot pretty sooon.... faster than under OSX or Windows.... this is a shame.. . I thought it was the keyoboard backlight at first but that doesn't seem to be it.

Also.. damn that fan is loud.


Any suggestions ?? (BTW My log out button -to right corner- doesn't show restart or turn off anymore.. weird)

---

### Post by emil.s on 2007-05-06
It's the same problem for me. And probably for everyone...

Se:
[https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty)

But if someone have a solution, it will be great! :)

---

### Post by The_Giver on 2007-05-06
I went to the linked page and I have no idea what that guy is talking about... for one.. how do i know if I have the mactel patch.. and two what do I do with the patch HE provides? .....

---

### Post by mustang on 2007-05-06
Both macbooks and macbooks pro's get hot under linux (and windows!) This is due to a lack of adequate power management. The good folks at mactel-linux are investigating the issue and of course, the linux kernel developers are attacking general power consumption issues (see 2.6.20.1 release notes). 

The only remedy as of now is to turn off features you're not using (bluetooth, wifi, isight) and to increase the default minimum fan speed. From [jason's website]("http://www.jasonparekh.com/2006/macbook-fan-control-in-linux/"), I dropped

```

sudo sh -c "echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed"

```

into /etc/rc.local so it gets executed everytime you startup. Then see [this]("http://ubuntuforums.org/showthread.php?t=398381&page=5") page to see what I did to get it saved across a suspend.

edit: and try to keep all your questions to one thread.

---

### Post by Chrisj303 on 2007-05-06
I have found that by installing "SMC Fancontrol" (Freeware App) on MacOSX, and cranking up the RPM, when i restart and boot into Ubuntu, the Fan speed (RPM) remains elevated.

Not a perfect fix, but it works for now.

SMCfancontrol can be found here: [http://www.macupdate.com/info.php/id/23049](http://www.macupdate.com/info.php/id/23049)


cheers,
chrisj303

---

### Post by tchorix on 2007-05-28
> **The_Giver said:**
>  (BTW My log out button -to right corner- doesn't show restart or turn off anymore.. weird)

I had this problem when I updated the machine of my wife from edgy to feisty (I use Gnome and she uses KDE). So, the problem was that gdm took the whole control for shutting down. You have to give it back to kde (I'm just guessing here what your problem is). I'm not in KDE right now, but I remember that is was a setting somewhere in the KDE Control Center, related to login-logout managers. Sorry for not giving more precise help. Maybe someone else here can

cheers
Tch

---

### Post by ronocdh on 2007-05-29
> **tchorix said:**
> I had this problem when I updated the machine of my wife from edgy to feisty (I use Gnome and she uses KDE). So, the problem was that gdm took the whole control for shutting down. You have to give it back to kde (I'm just guessing here what your problem is). I'm not in KDE right now, but I remember that is was a setting somewhere in the KDE Control Center, related to login-logout managers. Sorry for not giving more precise help. Maybe someone else here can

cheers
Tch

While on the subject, I should mention that the Beryl guide in my sig has a quick fix for what to do when the restart/shut down options don't appear in GNOME. Now, that refers to the script for running an XGL session, but perhaps it's another piece of the puzzle!

---

