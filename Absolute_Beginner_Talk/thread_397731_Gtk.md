---
title: "Gtk"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-03-31
I get this message when installing ALOT of programs...

checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK: Is gtk-config in path?

I was under the impression GTK was auto-installed with ubuntu? why am I having this error?

---

### Post by Bachstelze on 2007-03-31
Trying to install from source, huh ? Why don't you just apt-get your stuff ?

---

### Post by Warpnow on 2007-03-31
I need to install a mud client. I couldn't find any on the list of packages...

---

### Post by mcduck on 2007-03-31
I agree with HymnToLife, if possible you should just use the package manager to install things.

But anyway, your problem is that while GTK is installed, GTK development libraries are not and those are the ones that you need for compiling programs. Pretty much every time when you get errors that something is missing when compiling it's talking about development libraries, not the actual working programs.

---

### Post by Warpnow on 2007-03-31
Well, I found a couple. But when I did apt-get installl..I couldn't find them.

---

### Post by DSn0wMan on 2007-03-31
try this ```
 sudo apt-get install tf 
``` 

[http://packages.ubuntulinux.org/dapper/games/tf](http://packages.ubuntulinux.org/dapper/games/tf)

---

### Post by Warpnow on 2007-03-31
how do I access the program afterwards?

I'm very new to linux...

---

### Post by Perfect Storm on 2007-03-31
You need the libgtk2 -dev package.


Anyway look here if you want a full sourcelist which have almost anything: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by mcduck on 2007-03-31
> **Warpnow said:**
> Well, I found a couple. But when I did apt-get installl..I couldn't find them.

They are development libraries, just a big bunches of code, not any working programs. There would be no sense in putting them in your menus or anything like that :D When compiling the programs the compiler should be able to find & use them.

Anyway, there are plenty of MUD clients & servers installable with package manager:
```

$ apt-cache search mud
gmoo - a GTK+ based MOO (and MUD) Client
gnome-mud - The GNOME MUD client
koalamud - distributed MUD server
mmucl - Mark's MUd CLient
mordor - Multi User Dungeon game server
mudnames - Multi-User Dungeon name generator daemon
papaya - extensible MUD client
pennmush - text-based multi-user virtual world server
pennmush-common - common files for the PennMUSH virtual world server
pennmush-i18n - i18n support files for the PennMUSH virtual world server
pennmush-mysql - text-based multi-user virtual world server with MySQL support
tf - Tinyfugue MUD client for TinyMUDs, DikuMUDs, and LPMUDs
tintin++ - classic text-based MUD client
tinymux - text-based multi-user virtual world server
```

You might need to enable Universe & Multiverse repositories to get access to these.

---

### Post by Warpnow on 2007-03-31
the mud clients don't go to my menus, either, though...which makes using them difficult for a linux newbie like myself...


edit: Well, Gnome-Mud is added to my menu, but its the only one it seems.

---

### Post by Zguillotine on 2007-09-12
I cannot find PennMUSH or TinyMUX to run them. Okay, I am a newb on Ubuntu. So, I used the Synaptic Package Manager to download and install, but I cannot find them to run. They don't show up in the menus and I don't know how to start them up. 

Could someone help please? I have tried GnomeMUD and it is probably fine for some things, but I need the functionality that comes with the other two products. 

Thanks in advance for any help you might offer. 

-=ZG=-

---

### Post by Perfect Storm on 2007-09-12
You properly need to launch them through the terminal. Try with their names (lower case letters)

or finding where the bin name for it.

locate XXXXX

---

