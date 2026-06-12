---
title: "How do I get the older Gnome 2 UI?"
date: 2014-07-27
forum: Apple Hardware Users
---

### Post by jacatone on 2014-07-27
I have Lubuntu 12.04 LTS for PowerPC installed on an old Mac Powerbook laptop. How would I get the older Gnome 2 user interface installed? The one with the Applications, Systems, etc. on the top taskbar. I always liked that setup. Thanks.

---

### Post by ibjsb4 on 2014-07-27
What about Gnome Classic (also known as Fallback)

I should add ..
If you just want just the desktop without the extra packages:
```
sudo apt-get install --no-install-recommends gnome-session-fallback
```

[http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html)

[URL="https://help.ubuntu.com/community/PreciseGnomeClassicTweaks"]https://help.ubuntu.com/community/PreciseGnomeClassicTweaks

[/URL]

---

### Post by jacatone on 2014-07-28
Cool, would this automatically load the Gnome 2 UI or give me a choice on which window manager to choose on boot up?

---

### Post by oldfred on 2014-07-28
More info.
You should get choice on login screen. 
You click on the little icon/gear/logo in upper right corner to choose which desktop.
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

 [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)
You can reset gnome-panel settings to default:
dconf reset -f /org/gnome/gnome-panel/
[http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04](http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04)

---

### Post by ibjsb4 on 2014-07-28
Just to be clear, in 12.04 its called Fallback and in 14.04 the name was change to Flashback.

Your running 12.04 so you will use Fallback.  Which has the gnome2 look, but is really gnome3.

And yes, you choose your desktop at the login screen by clicking on the icon.  Choose 'no effects' and this will give you the metacity window manager.

---

### Post by jacatone on 2014-07-28
Is there a way to have this done automatically rather than my having to select it each time?

---

### Post by oldfred on 2014-07-29
You only have to select if you want to change from what you used last time.

---

