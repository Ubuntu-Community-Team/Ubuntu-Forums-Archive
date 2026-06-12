---
title: "Help.... (Solved)"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by AlMaSoUdI on 2005-11-11
hey guys i need a help lpz
when i write commands in the terminal it show some errors 
like when i write this:
sudo apt-get update
this will show:
[COLOR="DarkRed"]W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR]
also when i want install programs same thing happen!!!
so what shoul i do ???:confused:

---

### Post by Remmelas on 2005-11-11
well, to start, you could disable the hoary-backports lines in your /etc/apt/sources.list by editing them and putting a comment in front of those lines.  I'm in no position to know, but it looks like that mirror perhaps no longer mirrors hoary backports?

---

### Post by AlMaSoUdI on 2005-11-11
i don't get what you mean???!!!:confused: :confused: :confused: 
can you expline more plz

---

### Post by Remmelas on 2005-11-11
indeed.
from a terminal window(because i'm a terminal junky and don't know another way)
```
sudo gedit /etc/apt/sources.list
```
look for lines in that file that have the words backports in them.  Example from my file
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

and change them so that they have a '#' in front of them like so
```
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

save the file, and then run ```
sudo apt-get update
```
and those error messages should be gone.

---

### Post by AlMaSoUdI on 2005-11-12
thanks alot brother :D 
but way i have to put "#"
can you expline it plz :)

---

### Post by Kvark on 2005-11-12
Lines that start with # are ignored by computer programs. They are either comments written in English for humans to read or in this case disabled until a human enables them by uncommenting (removing the #) them.

---

### Post by grim918 on 2005-11-12
i had that same problem with my installation. by adding the # to comment out the backports should solve the problem. it did for me.

---

### Post by AlMaSoUdI on 2005-11-13
thanks guys

---

