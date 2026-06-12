---
title: "GNOME failure"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by cancertoast on 2007-12-22
Ok guys, I really have no clue as to what is going on.  I was trying to install beagle and followied the instructions I looked up (and from my limirted exp they would not cause this problem) and rebooted.  All of a sudden I get these popup boxes (along with large-fonted applications, as well as a black wallpaper for my desktop):
```

GConf error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/UNKNOWN:1.0
All further errors shown only on terminal

```

```

An error occurred while loading or saving configuration information for Nautilus. Some of your configuration settings may not work properly.


```

```

An error occurred while loading or saving configuration information for gnome-settings-daemon. Some of your configuration settings may not work properly.


```

```

An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.


```

I get this same error for 'gnome-session', 'nm-applet', 'vino session', 'update-notifier', and 'gnome-panel'.



Does anyone care to lend me a hand?  Otherwise I have no recourse but to do what I know will work for a fact, reformat.

---

### Post by blueridgedog on 2007-12-22
After 50 views and no reply, I can only think a fresh install was well, however, you may get mileage out of sudo dpkg-reconfigure xserver-xorg

---

### Post by cancertoast on 2007-12-23
Please explain further.  I have no doubt that if I went /etc/home/michael/games/etqw in the CLI it would work.... the failure is in the GUI....  You would think that this would be something easy to fix...

---

### Post by blueridgedog on 2007-12-23
I agree that your errors appear to be in the windowing environment, but that is composed of two parts in Linus, and X server and a desktop environment, my suggestion to re-run the configuration portion of the X server was sort of a very long shot gamble - the only suggestion I could come up with.

I don't see the connection with Beagle, though, as that is just and application and should not have screwed with gnome so badly.

You may consider posting in the desktop group as I bet there are some more advanced xwindow/gnome people there.

---

### Post by chilledraven on 2008-01-12
I've exactly the same problem... exactly (though I didn't install beagle). I'm starting to think a fresh installation may be the only solution.

---

