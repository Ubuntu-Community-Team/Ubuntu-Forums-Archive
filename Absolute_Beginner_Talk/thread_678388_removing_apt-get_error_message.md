---
title: "removing apt-get error message"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by mitch_feaster on 2008-01-25
I'm running ubuntu 7.10 server and when I tried to install some package
a while back (I don't even remember which package originally gave me
the error) apt-get wasn't able to do the whole install.  Anyways, every time
I install another package I get that same error message echoed back to me,
and now there have been several other packages that haven't installed
correctly and have just been appended to the list (see output below.)
This is what I get when I run sudo dpkg --configure -a (obviously). It's
also the exact same message I get anytime I install anything at all with
apt-get.

mgalgs@galgz:~/hw/Math_3310/hw2$ sudo dpkg --configure -a
Setting up dbus (1.1.1-3ubuntu4) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 winefish depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vim-full:
 vim-full depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 vim-full depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing vim-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 libgnomevfs2-0
 libnautilus-extension1
 libgnome2-0
 winefish
 vim-full
 libbonoboui2-0
 libgnomeui-0
 evince


thanks in advance for the help.

---

### Post by david_kt on 2008-01-25
I ever faced this problem before but I could not really remember what I have done to solve it. May you could try:

```
sudo apt-get autoremove
```

and make sure you take note of what it removes (you could copy the terminal output (using ctrl+shift+c) and paste it to any word proccessor (using ctrl+v)) . After that either you install back the application that you need, or you just need to install the meta package:

```
sudo apt-get install ubuntu-desktop
```

if it removes ubuntu-desktop meta package as well. If you are using kubuntu/xubuntu/edubuntu then you should replace ubuntu-desktop with related dekstop you are using.

DK

---

### Post by mitch_feaster on 2008-01-26
didn't really want to install all that, i'm just running a server, but oh well
I gave it a try and it got this far...

Setting up cupsys-common (1.3.2-1ubuntu7.5) ...
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by david_kt on 2008-01-26
Sorry I did not see that you installed server version so as there is no desktop meta-package.

But did you run sudo apt-get autoremove? If yes, did it succesfully remove all the unconfigured package? If yes, you just need to re-install the package remove by the autoremove.

DK

---

### Post by mitch_feaster on 2008-01-28
yes I ran sudo apt-get autoremove and it didn't remove anything.

---

### Post by RomeReactor on 2008-01-28
Hi. Try:
```
sudo aptitude install -f
```

---

### Post by mitch_feaster on 2008-01-29
Still no luck :(
All I want is to get rid of that pesky message that comes up whenever I use apt-get.
I think the error all started with dbus but I'm not sure.  Now there are just other
packages that don't configure correctly and they get appended to that list that comes
up every time I install something (even on a successful installation.)

Here's my output from sudo aptitude install -f

mgalgs@galgz:~/hw/Math_3310/tryit$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been kept back:
  initramfs-tools initscripts
The following partially installed packages will be configured:
  cupsys dbus evince libbonoboui2-0 libgnome2-0 libgnomeui-0 libgnomevfs2-0
  libnautilus-extension1 vim-full winefish
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dbus (1.1.1-3ubuntu4) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 winefish depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 winefish depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 winefish depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vim-full:
 vim-full depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 vim-full depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 vim-full depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 vim-full depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing vim-full (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 dbus
 libgnomevfs2-0
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libnautilus-extension1
 evince
 winefish
 vim-full
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up dbus (1.1.1-3ubuntu4) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 winefish depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of vim-full:
 vim-full depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 vim-full depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing vim-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 libgnomevfs2-0
 libnautilus-extension1
 libgnome2-0
 winefish
 cupsys
 vim-full
 libbonoboui2-0
 libgnomeui-0
 evince
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
mgalgs@galgz:~/hw/Math_3310/tryit$


Thanks for the help.

---

### Post by RomeReactor on 2008-01-29
What was the last thing you installed successfully, and what was the first you tried to install that started giving you the error message? A lot of Gnome libraries are showing up in your output since the first post. Were you trying to install the Ubuntu desktop, or at least Gnome, or a graphical application?

---

### Post by mitch_feaster on 2008-02-02
I don't really remember what I've installed successfully since it started giving
these error messages but I've installed quite a few things.  I think it all
started when I was trying to install winefish, a latex editor but I've since
installed it and it's working fine.  I run some graphical programs over ssh
(including winefish) but I don't use the actual server to run anything
graphical (I don't sit at it and start up X and stuff).
I think the first error I received was with 'dbus'.

---

### Post by jan quark on 2008-02-02
try

```
sudo apt-get -f install
```

---

### Post by mitch_feaster on 2008-02-05
no luck with sudo apt-get -f install
same error message.

---

### Post by sphoid on 2008-02-18
Apologies for reviving an old thread but I'm having this same problem and I'm wondering if there was ever a resolution?

---

