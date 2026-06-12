---
title: "Weird message when starting gsynaptics!"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Kunstar on 2007-04-22
I've been reading through  these forums trying to work out how to turn off my laptop touchpad...so i d/l gasynaptics and i got the following message when started it from system>preferences:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Could someone help me out!

PS I'm a newbie!

---

### Post by annda on 2007-04-22
you need the terminal for this. first type (or better copy & paste CTRL+SHIFT+v or middle click to paste in the terminal):

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

this will back up an important system file that you will have to change.in case something goes wrong, you will be able to restore the backed up file from the command line:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

open the file like this:

```
gksu gedit  /etc/X11/xorg.conf
```

find the device section for your touchpad and add this line:

```
Option "SHMConfig" "true"
```

you may also need to change the driver to "synaptics", i don't remember if gsynaptics will do it on it's own, or whether it has to be done manually.

save the file. reboot or restart the x server by CTRL+ALT+BACKSPACE.

---

