---
title: "&quot;No Screens Found&quot; help"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by neologism on 2007-02-23
hey guys, 

obviously i'm new to ubuntu, and i'm having a bit of trouble getting kubuntu running.  everything installs fine, but during the boot i get the 'no screens found' error from x-window and get stuck at the command prompt and i can't seem to get around it.  8800gtx hooked to either viewsonic lcd or westinghouse lvm-37 lcd tv with either DVI or VGA cables have same effect.  during the install, i selected most of the lower resolutions for x-window, both of which are compatible with the tv and monitor.  i think the refresh rate may be set to 70Hz (monitor info upon signal detection).  i try to run either 'xorgconfig' or 'xorgcfg' but ubuntu tells me the path doesn't exist.  i've updated both ubuntu, xorg (most recent version, but not last weeks release) and installed nvidia drivers with no change.  anybody have any ideas?  i've also tried fedora, but with no luck; i just get a blue line across the top of the screen after boot.

ps. all i know about linux is from reading forums, so please spell out the command line exactly, cause i don't know what i'm doing.

Athlon64 3000+
DFI Lanparty NF4
2GB Mushkin
8800gtx
X-fi
ubuntu intalled on WD Raptor (with windowz)

---

### Post by netkid91 on 2007-02-23
Ubuntu is based on Debian, which uses deb-conf to handle package configurations, to reconfigure a package we use dpkg-reconfigure.  So to setup X you use:
sudo dpkg-reconfigure xserver-xorg
And off you go.

---

### Post by taurus on 2007-02-23
Log in from a console and at the prompt, run

```
sudo dpkg-reconfigure xserver-xorg
(If you're not sure about a question, just use the default.  And use **vesa **driver for your graphic card.)
startx
```

---

### Post by neologism on 2007-02-23
ok, i'll give it a shot.  thanks for the patience with the noob.  are there any settings in particular i should be concerned with that aren't obvious to a windows user or is auto config?

thanks dudes.

---

### Post by netkid91 on 2007-02-23
You should be able to take care of most everything, the only thing that might get confusing is the video card driver.  It looks like you have an NVidia card, so if you don't have the official NVidia drivers installed select the "NV" Driver at the list.

---

