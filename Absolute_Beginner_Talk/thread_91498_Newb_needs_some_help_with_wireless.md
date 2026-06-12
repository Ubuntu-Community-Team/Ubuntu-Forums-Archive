---
title: "Newb needs some help with wireless"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by wildthing2022000 on 2005-11-17
I need some help with installing the ndiswrapper 1.5 on to ubuntu. This is a dumb but necessary question, but how do you install it? I've tried using this link
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
but the furthest I got was to make distclean and it doesn't go any further than that, it just tells me that it can't do it. When it says "Go to source-directory" does that mean the extracted folder or outside because I can't get it to work either way. Did I do something wrong? My laptop is a 3077WM compaq presario
with a broadcom 802.11 b/g WLAN.

---

### Post by tseliot on 2005-11-17
Try these commands:

```
sudo apt-get install ndiswrapper-utils

sudo apt-get install linux-restricted-modules-'uname -r'
```

BTW if you need a graphical interface for your Wifi card: [http://ubuntuforums.org/showthread.php?t=73563]("http://ubuntuforums.org/showthread.php?t=73563")

EDIT: try also these guides: [http://www.ubuntuforums.org/showthread.php?t=75451&highlight=wifi]("http://www.ubuntuforums.org/showthread.php?t=75451&highlight=wifi")

[http://www.ubuntuforums.org/showthread.php?t=85378&highlight=wifi]("http://www.ubuntuforums.org/showthread.php?t=85378&highlight=wifi")

---

### Post by danne on 2005-11-17
simply go to your pcket manager and install "ndisgtk".
When you've done that, you'll find a new prog under system called windows wireless drivers..now simply add a new wificard by loading the .inf file from the windows driver and there you go....
the only thing you have to do now is activate your card..
when it doesn't work..be sure to have no other wireless cards installed so you certainly avoid conflicts...

bye!!:cool: :cool:

---

### Post by wildthing2022000 on 2005-11-18
[QUOTE=tseliot]Try these commands:

```
sudo apt-get install ndiswrapper-utils

sudo apt-get install linux-restricted-modules-'uname -r'
```

BTW if you need a graphical interface for your Wifi card: [http://ubuntuforums.org/showthread.php?t=73563]("http://ubuntuforums.org/showthread.php?t=73563")

EDIT: try also these guides: [http://www.ubuntuforums.org/showthread.php?t=75451&highlight=wifi]("http://www.ubuntuforums.org/showthread.php?t=75451&highlight=wifi")

[http://www.ubuntuforums.org/showthread.php?t=85378&highlight=wifi]("http://www.ubuntuforums.org/showthread.php?t=85378&highlight=wifi")[/QUOTE]

Edit- I know what uname it is but the second line doesn't work. It gives me the can't find the package error.

---

### Post by wildthing2022000 on 2005-11-18
[QUOTE=danne]simply go to your pcket manager and install "ndisgtk".
When you've done that, you'll find a new prog under system called windows wireless drivers..now simply add a new wificard by loading the .inf file from the windows driver and there you go....
the only thing you have to do now is activate your card..
when it doesn't work..be sure to have no other wireless cards installed so you certainly avoid conflicts...

bye!!:cool: :cool:[/QUOTE]

Not there so I had to d/l it. BTW - how do you install .deb files?

---

