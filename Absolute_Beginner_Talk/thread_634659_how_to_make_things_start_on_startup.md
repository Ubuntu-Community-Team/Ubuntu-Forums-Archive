---
title: "how to make things start on startup?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by twist2b on 2007-12-07
ok like what file do you get to make it run on startup?
i got kiba dock... and i want it to load on startup everytime.... and screenlets dont load on startup either.... i know you add it to session in prefrences... but what file do you add....

im using gnome and thank you!

---

### Post by Tristicus on 2007-12-07
You have to type a command I think, such as "oy.desklets.start.tray." or something...

---

### Post by Flying caveman on 2007-12-08
I use the System-Preferences-Sessions then under the startup programs tab you can add whatever you want.   You just need to know the command to start the app you want.

---

### Post by HDave on 2007-12-08
Goto System->Preferences->Sessions

and add a new item in there with the command "kiba-dock"

I use Kiba dock too and I love it...also used sessions to auto-start "conky"...also very cool program.

---

### Post by PmDematagoda on 2007-12-08
You can find the the proper file by using the Main Menu configurator found in System>Preferences>Main Menu, then go to the place of the main menu where the launcher is found and get it's information by double-clicking on it, then copy the "command" entry and paste it onto the Start-up programs command in the Sessions tool, after that you are good to go:).

---

### Post by twist2b on 2007-12-08
thanks a ton guys.... tihs is awsome! yea now i can make any program run on startup.... this is awsome and super appriciated... hopefully i can give what you guys gave me in this forum!

---

### Post by PmDematagoda on 2007-12-08
> **twist2b said:**
> thanks a ton guys.... tihs is awsome! yea now i can make any program run on startup.... this is awsome and super appriciated...

No problem, we are glad to help:).

> hopefully i can give what you guys gave me in this forum!

That would be a great help:).

---

### Post by cookieforyou on 2007-12-17
Hi guys

I tried to add conky to my startup sessions as suggested above (System > Preferences > Sessions) and added it at startup but it does not stay.  I see conky on bootup but it disappears when my desktop completes booting up. If I do ```
ps aux|grep conky
```
I get ```
------     5836  0.0  0.1  10068  1996 ?        S    13:50   0:00 conky
------     5967  0.0  0.0   2976   752 pts/0    R+   13:53   0:00 grep conky

``` so it seems to be running, only in the background somewhere.
Any ideas?

EDIT: OK, found the solution to my problem here
[http://ubuntuforums.org/showthread.php?t=205865&highlight=autostart+conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=autostart+conky)
> This would start conky after 60 seconds of your login.

---

