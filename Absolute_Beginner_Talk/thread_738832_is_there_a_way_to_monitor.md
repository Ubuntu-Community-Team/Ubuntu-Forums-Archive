---
title: "is there a way to monitor"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-29
system specs like cpu and gpu temps in hardy?

---

### Post by hhhhhx on 2008-03-29
EDIT: for temps:
yes, you have to install the lmsensors :  [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

and then you will need something to display them, you can use the terminal, or there are a bunch of other things, like conky

---

### Post by chewit on 2008-03-29
you could always, right click on your taskbar and add an item. Select System monitor to watch your cpu and memory usage

---

### Post by mcduck on 2008-03-29
Depending on your hardware, simply running "acpi -V" from a terminal might tell your temperatures and fan speeds. (This only works if your hardware has a proper ACPI support).

If that doesn't work for you, you'll need to install and configure lm-sensors.

As soon as you have either one of these working, you should be able to use whatever graphical monitoring app you like to view your temperatures. Conky, Screenlets, gDesklets and gKrellm alre probably the most popular ones, but there are many others around, for example the nice Hardware Monitor-applet for Gnome's panel.

---

### Post by waspbr on 2008-03-29
you can get yourself some applets to do that, just check out this link

[http://ubuntuforums.org/showpost.php?p=4609189&postcount=772]("http://ubuntuforums.org/showpost.php?p=4609189&postcount=772")

note this only works in gnome, not in kde

---

### Post by bumanie on 2008-03-29
There's also a program called conky that can be configured to monitor many different proccesses. Look here for examples [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)
Conky can be installed via synaptic, but you have to use an already existing script or create your own. There is a huge forum thread also
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

