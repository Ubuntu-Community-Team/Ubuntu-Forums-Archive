---
title: "Boot-up problem"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by owmyshoe on 2006-04-04
I recently just installed 5.10 on my compaq presario v2000(AMD 64bit Turion 1.67ghz(or something close), 1.00GB of ram, and an 80 GB HDD)
With the exception of setting up the network (I was planning on settin up a wireless connection) it installs fine, but when it goes to boot (the only error read while loading was synching with the clock via the internet) I get a blue screen error telling me my graphical interface, xserv(or maybe it was xwindow) and gnome failed to load, and it goes black and displays only text. I can "log in" and sort of snoop around (it will recognize but not execute any commands e.g. /usr/*) is there anything I can do if I were to reinstall, or can I do anything through the text prompt?

---

### Post by meborc on 2006-04-04
after loging in you can type:

**dpkg-reconfigure -phigh xserver-xorg**

and try to reconfigure your xserver...

---

### Post by owmyshoe on 2006-04-04
now do you mean to type [in descendin order]
dpkg
reconfigure
phigh xserver
xorg

---

### Post by izmaelis on 2006-04-04
You started to threads for the same problem? :mrgreen: 
Check out what I said [there]("http://www.ubuntuforums.org/showthread.php?t=155020").

---

### Post by meborc on 2006-04-04
[QUOTE=owmyshoe]now do you mean to type [in descendin order]
dpkg
reconfigure
phigh xserver
xorg[/QUOTE]

no
i
mean
to
type
like
i
typed
:mrgreen: 

**dpkg-reconfigure -phigh xserver-xorg**

in
one
line

---

