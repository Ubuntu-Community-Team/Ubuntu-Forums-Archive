---
title: "[SOLVED] HELP messed up my desktop playing with appearnce settings"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-10-28
well i did it again played around and now i messed everything up. i changed some appearnce settings and emerald theme settings, and now when i log in i have a black desktop (see screenshot) after opening the preferences-->appearance window my desktop background etc is back (see second screenshot). but thats not all somehow everything that is on the desktop, like for example the screenshot files don't show up anymore. and i can't open my home directory or anything else thats under "Places -->" so I don't have my windows anymore :confused: can only access files through terminal at the time ??? i really don't know enough about linux to fix this so before i have to create a new user and reset everything i was hoping that someone might be able to help me out with this.

thx in advance

---

### Post by daimaru on 2007-10-28
anyone ? plz help this is really bad i dont want to reinstall everything.

---

### Post by daimaru on 2007-10-28
help plz does no one have any ideas? cant i just delete something in my homefolder lilke gnome settings or some such thing (sorry dont know too much about that) to get it back to normal?

---

### Post by krisfrajer on 2007-10-28
Try this:

go to /etc/X11 and then type:

grep sudo xorg.conf

After that you will have something like this:
#   sudo dpkg-reconfigure -phigh xserver-xorg

then type that line ommiting the "#" and that should reconfigure your desktop settings as original set by the installer initially. 
I hope this helps!

---

### Post by daimaru on 2007-10-28
no that's not it did that already ,  i think my desktop is just gone somehow i cant even right click it anymore , no menu shows up :confused: created new user and everything works fine but i dont want to install all programs again and go through all the config stuff again. i want to keep my current account. i tried all kinds of stuff already deleted the .themes .emerald .gnome .gnome2 .gnome2_private directories but no change
+

---

### Post by llamakc on 2007-10-28
Is Nautilus even running?

Open the run dialog with "ctrl-F2"  and type nautilus

and see what happens.

---

### Post by daimaru on 2007-10-28
running nautilus did nothing ...
so this is what i get greping it
```
ap@alita:~$ ps aux |grep nautilus
ap        7070 85.1  3.0 143892 63696 ?        R    16:15 239:02 nautilus --no-default-window --sm-client-id default2
ap        7190  0.0  0.0   2660   896 ?        S    16:15   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
ap        7720  0.0  0.4  30764  8384 ?        S    16:48   0:00 nautilus --no-default-window --sm-client-id default2
ap        7944  0.0  0.4  30764  8388 ?        S    16:49   0:00 nautilus --no-default-window --sm-client-id default2
ap        8275  0.0  0.4  30764  8388 ?        S    16:53   0:00 nautilus --no-default-window --sm-client-id default2
ap        8410  0.0  0.4  30764  8400 ?        S    16:54   0:00 nautilus --no-desktop file:///home/ap
ap        8452  0.0  0.4  30764  8404 ?        S    16:56   0:00 nautilus --no-desktop file:///home/ap
ap        8503  0.0  0.4  30768  8400 ?        S    17:01   0:00 nautilus --no-desktop computer:
ap        9017  0.0  0.4  30764  8400 ?        S    18:41   0:00 nautilus --no-desktop file:///media/sda1
ap        9317  0.0  0.4  30764  8388 ?        S    19:43   0:00 nautilus --no-default-window --sm-client-id default2
gg       10412 86.4  2.3 113904 49700 ?        R    19:50  57:17 nautilus --no-default-window --sm-client-id default2
gg       10482  0.0  0.0   2660   896 ?        S    19:50   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
gg       10868  0.0  0.4  30768  8388 ?        S    19:52   0:00 nautilus --no-default-window --sm-client-id default2
ap       11782  0.0  0.4  30768  8388 ?        S    19:56   0:00 nautilus --no-default-window --sm-client-id default2
gg       12941  0.0  0.4  30764  8388 ?        S    20:17   0:00 nautilus --no-default-window --sm-client-id default2
gg       13087  0.0  0.4  30764  8400 ?        S    20:18   0:00 nautilus --no-desktop file:///home/gg
ap       20340  0.0  0.0   2976   768 pts/1    S+   20:56   0:00 grep nautilus

```
ohoh i think that part about nautilus --no-desktop file and nautilus --no-default-window doesnt look good does it ?

---

### Post by daimaru on 2007-10-28
just for the fun of it i just reinstalled nautilus, but no change. well nautilus was fine when logging in as different user so there wasnt much hope anyway. but what config file under gnome might control nautilus i mean i must have messed up something so that now i dont have a desktop anymore. 

the only thing i did was delete my main menu bar (the one on the top ) and replaced it by creating a new one (long story i installed moomex theme and my buttons where suddenly huge -- and somehow i couldnt get them to normal 24pix size anymore)

---

