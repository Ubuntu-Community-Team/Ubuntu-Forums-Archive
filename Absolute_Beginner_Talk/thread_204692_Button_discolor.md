---
title: "Button discolor"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by loserboy on 2006-06-27
why do these buttons look like this?

---

### Post by FuturePast on 2006-06-27
Something to do with the interaction between the X (graphics) server and the graphics card. 

Happens to me, nothing to worry about.

---

### Post by loserboy on 2006-06-27
is there no way to make it stop?    it does that on all buttons all the time

---

### Post by xtacocorex on 2006-06-27
You need to add an option to the Device section identifying your monitor in your /etc/X11/xorg.conf:

```

sudo gedit /etc/X11/xorg.conf

```

```

Option       "RenderAccel"     "false"

```

The spaces between the options are supposed to be tabs.

To get the changes to show up, either restart or hit ctrl+backspace to restart X.

---

### Post by loserboy on 2006-06-27
:(  it didnt change anything

was the xorg.conf suppose to be an empty file?

---

### Post by xtacocorex on 2006-06-27
Crap.

My bad, I gave you the wrong file to edit. It should be /etc/X11/xorg.conf

Serves me right to be eating lunch while at work on my computer not doing stuff that I should be doing.

Sorry about that.

---

### Post by loserboy on 2006-06-27
lol hey at least you're helping me..... im surprised people dont see my name on the thread and go "ugh... not him again"

---

### Post by xtacocorex on 2006-06-27
There should be a section similar to the one below. Note that I found that section on the mailing list and since I'm not at home, I can't attach part of my xorg.conf file.

```

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M6 LY
[Radeon Mobility 9000]"
Driver "ati"
BusID "PCI:1:0:0"
Option "RenderAccel" "false"
EndSection

```

Don't copy that section because it'll screw up your file, I'd find the similar section and then paste in the option line.

Here is the thread for more reference [http://www.ubuntuforums.org/showthread.php?t=195583&highlight=renderaccel](http://www.ubuntuforums.org/showthread.php?t=195583&highlight=renderaccel)

---

### Post by loserboy on 2006-06-27
lol  i messed up x
how can i edit through command    i tried gedit but i guess its an x program

---

### Post by bruce89 on 2006-06-27
[QUOTE=loserboy]lol  i messed up x
how can i edit through command    i tried gedit but i guess its an x program[/QUOTE]
```
sudo dpkg-reconfigure xserver-xorg
```
Or you can edit it manually with ```
sudo nano /etc/X11/xorg.conf
``` and press Contol+X to quit it.

---

### Post by loserboy on 2006-06-27
there we go I put it under the wrong option spot, i put it under monitor.

that worked perfect  thanks you guys for the help

(for future reference is the nano command for editing any text files in terminal?)

---

### Post by xtacocorex on 2006-06-27
Glad to be of help.

Yes, nano is a text editor for the command line. It is not the only one, there are many:
 - vi
 - emacs
 - joe
 - pico
 - nano
to name a few. Each has their own way of doing things. vi and emacs are the most powerful of the ones listed, but require a decently steep learning curve to be comfortable with them.

---

