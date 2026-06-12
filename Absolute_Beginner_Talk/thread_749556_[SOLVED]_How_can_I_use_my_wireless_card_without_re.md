---
title: "[SOLVED] How can I use my wireless card without rebooting?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by KIAaze on 2008-04-08
I have a PCMCIA wireless card.
The problem is that whenever I want to use it, I have to boot with it plugged in. Otherwise it remains deactivated.

Is there a way to start/stop the card without rebooting as in Windows?

---

### Post by pseudo-random on 2008-04-08
Yeah. Use iwconfig to determine the name of your card (eg eth1 or ath0 ...) Then use ifconfig to bring it up/down
```
ifconfig ath0 up
```

---

### Post by KIAaze on 2008-04-08
Thanks.
Any way to do it through the GUI?

---

### Post by bodhi.zazen on 2008-04-08
Use Network manager, should be an applet on your panel, upper right.

System-->Administration-->Networking

[img]https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?action=AttachFile&do=get&target=NetworkAdmin1.png[/img]

[img]https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?action=AttachFile&do=get&target=NetworkAdmin2.png[/img]

---

### Post by KIAaze on 2008-04-08
Mmh, somehow I fear this won't work. I'll try it when I get home, but the Network manager was the first thing I tried last time, and if I remember correctly the device isn't even listed in there if I plug it in after boot. (the lights on the wifi-card are off too)

---

### Post by KIAaze on 2008-04-10
It doesn't work. :/
The problem is that it isn't even powered on if I plug it in after booting. It doesn't show up in lspci.

Here's what I get when it's on:
```
$lspci
...
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
...

```

---

### Post by bodhi.zazen on 2008-04-10
My guess is you need to load the driver, ie modprobe.

I do not know the drivers for the card.


If you do not know the modules, with the card active, use ```
lsmod
```

then, with the card off and plugged in, try modprobe.

```
modprobe <module
```

Like in step 6 of this how-to :

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

If that works, you can then write a script ...

---

### Post by KIAaze on 2008-04-10
Ok, problem solved and I even made a "GUI" for it (sort of... ^^).
To turn the card on:
```
pccardctl insert 0
```
To turn the card off:
```
pccardctl eject 0
```

Here's a nice little script to do this:
```
#!/bin/bash
CARDON=$(lspci | grep -c Atheros)
if [ $CARDON -eq 0 ]
then
	zenity --question --text "CARD OFF: Do you want to turn it on?" && gksudo -m "Turn PCMCIA card on" pccardctl insert 0
else
	zenity --question --text "CARD ON: Do you want to turn it off?" && gksudo -m "Turn PCMCIA card off" pccardctl eject 0
fi

```
It requires zenity which can be installed by doing:
```
sudo apt-get install zenity
```

To use it through a "GUI", I created a custom launcher in the Gnome panel.
A real system tray icon would be nicer, but I don't know how to create one yet. :/

edit:
Found some interesting tutorials:
[http://www.gnome.org/projects/ORBit2/appletstutorial.html](http://www.gnome.org/projects/ORBit2/appletstutorial.html)
[http://developer.gnome.org/doc/tutorials/applet/index.html](http://developer.gnome.org/doc/tutorials/applet/index.html)
[http://www.pygtk.org/articles/applets_arturogf/](http://www.pygtk.org/articles/applets_arturogf/)
Maybe I'll make an applet one day. :)
So many things to do and so little time...

---

### Post by KIAaze on 2008-04-20
I created a little gnome applet using python+pygtk. :)
It's not perfect yet as it doesn't resize with the panel bar (it's made for the default panel size (24 pixels)).
I used the jockey.svg image from the jockey-common package.

The applet allows inserting/ejecting PCMCIA devices through the GUI and also checks if a PCMCIA device is active every second to update the applet image.

Any help on improving the daemon-like behaviour or the applet resizing is welcome. :)

I'm releasing this under the GPL. To get the source code, just extract the contents of the .deb. It's just some python scripts after all.

---

