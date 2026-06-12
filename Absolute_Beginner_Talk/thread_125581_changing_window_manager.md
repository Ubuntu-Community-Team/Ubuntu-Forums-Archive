---
title: "changing window manager"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-02-04
Is it worth it to install xfce. How much faster would it be then the default that comes with ubuntu. I also want to replace gnome, I was going to use blackbox. Is this a good idea ?

Could someone post the commands to install both of these ? Thanx :)

---

### Post by Klaidas on 2006-02-04
What's wrong with ubuntu defaults? :)

---

### Post by xXx 0wn3d xXx on 2006-02-04
nothing is really "wrong" but xfce is faster (so i've heard) and so is blackbox. This computer is 8 years old which is why I was thinking about switching.

---

### Post by bluevoodoo1 on 2006-02-04
[QUOTE=MasterChief1234]Is it worth it to install xfce. How much faster would it be then the default that comes with ubuntu. I also want to replace gnome, I was going to use blackbox. Is this a good idea ?

Could someone post the commands to install both of these ? Thanx :)[/QUOTE]

```

sudo apt-get install blackbox

```

(you might want bbconf too, helpful for editing styles and menu)
```

sudo apt-get install blackbox bbconf

```

I think xfce is

```

sudo apt-get install xfce4

```

There are some other packages needed with it, apt-get should list them... if not try searching for xfce with Synaptic.


I love blackbox, BUT you have to configure it yourself AND it's very minimal... (two of the reasons why I like it!)

---

### Post by xXx 0wn3d xXx on 2006-02-04
blackbox won't install....and when I use fluxbox the screen res is all messed up and I have no desktop :(

---

### Post by bluevoodoo1 on 2006-02-04
I haven't used fluxbox, so I wouldn't be much help with it, but what do you mean by "blackbox won't install?"

---

### Post by xXx 0wn3d xXx on 2006-02-04
[QUOTE=bluevoodoo1]I haven't used fluxbox, so I wouldn't be much help with it, but what do you mean by "blackbox won't install?"[/QUOTE]

When I try to install it I get: that it doesn't exist :(

---

### Post by xXx 0wn3d xXx on 2006-02-04
[QUOTE=MasterChief1234]When I try to install it I get: that it doesn't exist :([/QUOTE]

here's the full message,

> Reading package lists... Done
Building dependency tree... Done
Package blackbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package blackbox has no installation candidate

---

### Post by bartbes on 2006-02-04
> 
Reading package lists... Done
Building dependency tree... Done
Package blackbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package blackbox has no installation candidate 
Looks like there is or something wrong with your sources list or the servers are/were down. Try [code]apt-get update[/quote] (as apt-get said) and do this a few times if there are errors, if it's still not working it's one of the above

---

### Post by xXx 0wn3d xXx on 2006-02-04
yea I'm screwed:

I got this: E: Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied)

edit: I got it :) I had to fix my sources list.

edit again: I get this:

Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  bbkeys
The following NEW packages will be installed:
  blackbox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/376kB of archives.
After unpacking 1200kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 109321 files and directories currently installed.)
Unpacking blackbox (from .../blackbox_0.70.0-4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/blackbox_0.70.0-4_i386.deb (--unpack):
 trying to overwrite `/usr/bin/bsetroot', which is also in package fluxbox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
postrm called with unknown argument `abort-install'
Errors were encountered while processing:
 /var/cache/apt/archives/blackbox_0.70.0-4_i386.deb

---

### Post by bluevoodoo1 on 2006-02-04
Yeah, I've encountered problems with trying to have Fluxbox and Blackbox installed at the same time... perhaps uninstall fluxbox?

---

### Post by xXx 0wn3d xXx on 2006-02-04
ok it installed :) I have a few questions though: can I have the applications System and Places menus again ?, my screen resolution is messed up. Can I fix it ?, and other then that it is amazing. On my 8 year old computer firefox usually takes 20-25 seconds to start. This time, with blackbox, it started in under 3 seconds !!!

---

### Post by xXx 0wn3d xXx on 2006-02-04
can I have desktop shortcuts with this ?

---

### Post by bluevoodoo1 on 2006-02-04
[QUOTE=MasterChief1234]ok it installed :) I have a few questions though: can I have the applications System and Places menus again ?, my screen resolution is messed up. Can I fix it ?, and other then that it is amazing. On my 8 year old computer firefox usually takes 20-25 seconds to start. This time, with blackbox, it started in under 3 seconds !!![/QUOTE]

to start gnome panel:

```
gnome-panel &
```

to stop it:
```
killall gnome-panel
```

You might want to add that code to your menu with bbconf. 

system > pref > screen resolution 
to fix the resolution perhaps?

---

### Post by xXx 0wn3d xXx on 2006-02-04
[QUOTE=bluevoodoo1]to start gnome panel:

```
gnome-panel &
```

to stop it:
```
killall gnome-panel
```

You might want to add that code to your menu with bbconf. 

system > pref > screen resolution 
to fix the resolution perhaps?[/QUOTE]

thanks :) can I have desktop icons or something like the old gnome menu ? And can I put icons on the bar at the bottom ?

---

### Post by bluevoodoo1 on 2006-02-04
[QUOTE=MasterChief1234]thanks :) can I have desktop icons or something like the old gnome menu ? And can I put icons on the bar at the bottom ?[/QUOTE]

Hmm I'm not sure about icons. Blackbox is a window manager, you'd have to get some sort of 'desktop' app. You'd have to use a third-party application like rox-filer. I've never used it, but here it is...

[http://rox.sourceforge.net/desktop/static.html](http://rox.sourceforge.net/desktop/static.html)

you mean putting icons on the gnome-panel?? If yes, then yes you can put icons on the gnome panel, simply right click on it and select "add to panel."

I have a bunch on mine (when I use it, which isn't too often)...

(screenshot attached of icons on gnome-panel)

---

