---
title: "kde killed my gnome"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-10-18
So, I installed kubuntu-desktop to try out kde some and when I tried to change back to gnome it didnt work. I log in to gnome and only get the background color and empty grey taskbars that pop ups and pop in and regular intervals.. and it doesnt go any further..

Please help :(

---

### Post by ATAQ on 2006-10-18
stop X, and then try /etc/init.d/gdm start as Su

Dunno, might work!

---

### Post by linear on 2006-10-18
If that doesn't work, try re-installing ubuntu-desktop.

---

### Post by jcrnan on 2006-10-18
none of that works. If I try startign gnome in failsafe mode the same happens but before the first "Blink" a warning message box with no text it in it pops up (but dissapears when it blinks back in).

Please help me here :( I really dont like it in kde and I want my gnome back.

---

### Post by Josey on 2006-10-18
Did you possibly install new themes at your last gnome session?
Try creating a new user acct while in kde and see if that acct gets you into gnome.

---

### Post by jcrnan on 2006-10-18
nope, didnt install anything new except kubuntu-desktop in my last gnome session. I'll try the account thing.

---

### Post by jordanmthomas on 2006-10-18
Try deleting this file from your home directory:
```
rm ~/.gtkrc-2.0
```

If you have told KDE to use certain GTK themes, Gnome is usually a jerk about it.

---

### Post by jcrnan on 2006-10-18
so, I made a new account and logged into that in gnome, no problems. and now it also let me log into my other account. However, the notification are with the small icons for different programs, batter indication, volume control, etc isnt working. it gives me lots of errors and all those stuff go away.

The panel encountered a problem while loading "OAFIID:GNOME_Panel_WirelessApplet".

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".

etc.



edit: for some reason the mouse icon that shows waiting time is the ugly kde one, not the gnome one :S
jordan: I didnt tell kde to use gtk themes.


edit: No gtk programs work at all. (doesnt include nautilus, but does include system config windows)

edit: more oddities: The gnome theme no longer touches the taskbars, only the windows.

---

### Post by jd65pl on 2006-10-18
sounds like you stuffed gnome-settings-daemon, it did the same just going to play the waiting game until edgy!!!

---

### Post by jordanmthomas on 2006-10-18
So does ~/.gtkrc-2.0 not exist?
It will not do any harm to delete it if it does, as it is probably what is causing your problems.
It just tells GTK what theme to use if there is no gnome-settings-daemon running.

As for your applets not working, maybe try
```
sudo dpkg-reconfigure gnome-applets
```
It will ask you a question about your cpu frequency...just answer it as you wish.
It should reconfigure the applets, maybe fixing them.

---

### Post by Zeddicus on 2006-10-18
> **jcrnan said:**
> jordan: I didnt tell kde to use gtk themes.

For the record, you don't have to.  Kubuntu-desktop includes a gtk theme (enabled by default in kubuntu) which makes your gtk apps look like QT (KDE) apps.

> **jcrnan said:**
> edit: more oddities: The gnome theme no longer touches the taskbars, only the windows.

Did you delete the gtkrc-2.0 file like mentioned?  I understand that you didn't intentionally change it, but, well... that might not matter, as I mentioned above. :)

Otherwise, the only thing I can think of is something getting screwed up in your ~/.gnome2 directory.  I've had issues with that before... usually deleting it clears it up, though it removes your personal settings.  You could try renaming that folder (don't delete it, just in case!) to see if reverting to the defaults clear up your issue (assuming you're not worried about losing your Gnome customizations).

---

### Post by jcrnan on 2006-10-18
well, I deleted the file and reconfigured the applets and both applets and gtk programs work. It seems like it made beryl a bit unstable tough but I can live with that. It prolly just changed something in xorg or something weird. anyways, what happens if I switch to kde via beryl manager?

---

### Post by jordanmthomas on 2006-10-18
It shouldn't have made beryl unstable or played with xorg.conf, but...who knows?

If you switch to kwin while running beryl in gnome nothing bad will happen, except you will have a better window manager than metacity.

---

### Post by janbockaert on 2006-11-18
thanks jordanmthomas, same problem, and same solution (delete gtkrc) worked here.

I guess gtkrc is useful for people who only use kde, but for those who switch between the desktops, it makes things to difficult.

Now i'll can look for a new u-splash.

When installing the kubuntu-desktop package with synaptic, it does ask if you want to keep using gdm, it should also ask if u are planning to keep using gnome (and not install gtkrc if you say yes, and it should ask if you want the blue kubuntu u-splash.

hmmm, sounds like somthing i could post on launchpad.

---

