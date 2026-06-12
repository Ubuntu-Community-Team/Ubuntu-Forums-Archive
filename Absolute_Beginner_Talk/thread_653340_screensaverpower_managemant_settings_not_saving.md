---
title: "screensaver/power managemant settings not saving?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-29
My screen goes black at 10mins of inactivity even though I dont have the screensaver set to 'active' and the power-managemant settings are set to 'never' for putting the monitor to sleep.

Pretty damn annoying when watching a DVD!

---

### Post by MangasColoradas on 2007-12-30
Session wasnt being saved so I have done preferences>>sessions>>session options and ticked 'save current apps'. That might fix it.

---

### Post by MangasColoradas on 2007-12-30
That didnt work and its definitely power management as I uninstalled screensavers.

Is this a bug?

---

### Post by MangasColoradas on 2008-01-01
[IMG]http://img90.imageshack.us/img90/4079/bellybump1yn8.gif[/IMG]

---

### Post by FoxOne on 2008-01-01
I second that bump, same problem in xubuntu 7.10, but what's odd is my wife's machine 6.06LTS doesn't have this issue.

---

### Post by joebwan on 2008-01-04
I'm having this same problem on 7.10.  The settings appear to have saved (in that if I go into the menu the new selections are ther) but the behavior doesn't change, and if I log out and log back in again I see the old settings (10 minutes, blank screen).

---

### Post by MangasColoradas on 2008-01-05
Still doing it.

Could it be just a problem with the Power Management GUI?

Would it be possible to fix from the command line?

Anything I can change in BIOS, maybe ACPI?

---

### Post by ant1060 on 2008-01-05
Hi!
I had a similar problem a while back and some kind ubuntu-er gave me this solution :
Type the following in a terminal

killall gnome-screensaver
gnome-screensaver --display=:0

This will enable your screensaver and power management settings to be applied for as long as your session lasts : if you reboot, you'll have to do the process again!

Hope this works for you :)

---

### Post by MangasColoradas on 2008-01-05
Thanks, I will try it. :)

---

### Post by MangasColoradas on 2008-01-06
That didnt work as the problem isnt only the screensaver, it is the monitor being put to sleep.

The monitor actually goes into stand-by mode at about 20 mins, it must be a power management thing, not a screensaver thing.

---

### Post by MangasColoradas on 2008-01-06
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969)

---

### Post by MangasColoradas on 2008-01-06
I have just done as suggested in the link, I added


> Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection


to the xorg.conf. I waited 25 minutes and the screen had still not gone into stand-by.

I think it's fixed it but I will have to try it for longer....

If it isn't fixed I am going to disable 'power management' from session startups.

---

### Post by MangasColoradas on 2008-01-06
2 hours later and the screen remains on. :)

Of course, this hasnt actually fixed it because I cant use the power management settings as I would like to, but it does stop the monitor going into stand-by every 20 mins so it will have to do for now.

As it IS a bug and has been known about for over a year, how come it hasn't been fixed?

---

### Post by FoxOne on 2008-02-22
Because everyone is busy with this eye-candy kick. IMHO Compiz and Beryl get way more attention then is nesscary right now. And this isn't a knock at Canonical, I'm talking about the Ubuntu community as a whole. I wish my programming skills were more advance so I could contribute.

---

