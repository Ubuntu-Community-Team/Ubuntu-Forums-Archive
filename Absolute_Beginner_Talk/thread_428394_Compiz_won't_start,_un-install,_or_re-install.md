---
title: "Compiz won't start, un-install, or re-install"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-30
i was working on compiz the other day.  following a tutorial off the official compiz website that was supposed to enable extra plug-ins and settings.  the problem is that upon following one of the instructions, it partially un-installed compiz.  now it won't re-install through symantec.  any ideas?

when i try to install "compiz-gnome," it gives me this.
> 
compiz-gnome:
  Depends: compiz-gtk (=1:0.3.6-1ubuntu13) but 1:0.5.0-0ubuntu1 is to be installed


and if i try to completely un-install the seperate parts of compiz to get it off my system (i use beryl instead) it tell me it's going to remove desktop effects, compiz, and ubuntu desktop.  i'm fine with compiz and desktop effects dying, but from my research, ubuntu desktop's pretty important.  please help!

---

### Post by webjames on 2007-05-01
> **locke.dragon said:**
> i was working on compiz the other day.  following a tutorial off the official compiz website that was supposed to enable extra plug-ins and settings.  the problem is that upon following one of the instructions, it partially un-installed compiz.  now it won't re-install through symantec.  any ideas?

when i try to install "compiz-gnome," it gives me this.


and if i try to completely un-install the seperate parts of compiz to get it off my system (i use beryl instead) it tell me it's going to remove desktop effects, compiz, and ubuntu desktop.  i'm fine with compiz and desktop effects dying, but from my research, ubuntu desktop's pretty important.  please help!

you could try this instead:

```

sudo apt-get install beryl beryl-manager
beryl-manager
```

that should start beryl (like compiz), and you should have a diamond in your tray where you can look at the settings. if you right click on that icon you can change the default window manager from metacity, to beryl. for more information look at [www.beryl-project.org]("http://www.beryl-project.org")
make sure you have the restricted drivers installed, goto settings restrictive driver > and enable your grfx card drivers
hope this helps,

---

### Post by locke.dragon on 2007-05-01
i actually already have beryl, beryl-manager, and most of the beryl plug-ins installed.  it's working perfectly and i prefer it to compiz (been using beryl longer).  but i'd still like to either completely un-install or re-install beryl so i have the option.  if i can't do either of those things, can someone at least tell me how to remove it from the list of window managers in beryl-manager?  (right click on beryl-manager, window managers, and compiz is still there even though it's inoperable)

---

### Post by locke.dragon on 2007-05-08
bump

---

### Post by locke.dragon on 2007-05-08
when i try to use teminal to re-install compiz-gnome (one of the two missing compiz files) i get this...

```

link@aperturescience:~$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but 1:0.5.0-0ubuntu1 is to be installed
E: Broken packages
link@aperturescience:~$ 

```

when i try to install compiz-gtk (the other missing compiz file) i get this...

```

link@aperturescience:~$ sudo apt-get install compiz-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  imlib11 krita-data space-orbit-common libsdl-erlang vorbis-tools
  airstrike-common libflac++5c2 liboggflac3 trigger-data kdebase-data
  mysql-common pouetchess-data ntp-simple libogg-dev libcurl3-gnutls
  libwavpack0 libmysqlclient15off unixodbc matchbox-common setserial libkonq4
  odbcinst1debian1 libmikmod2 kdebase-bin ladspa-sdk libmatchbox1 lm-sensors
  libphysfs-1.0-0 erlang-dev libtunepimp3 ntp libifp4 galeon-common docker sox
  imlib-base libjabberoo0c2a libsidplay1 erlang-nox erlang-mode mpg321 libpq4
  libraptor1 erlang-src liblrdf0 libgconfmm-2.6-1c2 erlang-examples
  libntfs-3g0 libgtkglext1 libid3-3.8.3c2a libglademm-2.4-1c2a libnjb5
  libltdl3 erlang-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
link@aperturescience:~$ 

```

maybe that'll help you all help me.  please help.

---

### Post by locke.dragon on 2007-05-08
[http://compiz.org/Ubuntu_Installation_Guide](http://compiz.org/Ubuntu_Installation_Guide) 
that's the guide i tried to follow to install extra compiz stuff.  that's when it went wonkie.
i have feisty and was following those instructions.

---

