---
title: "can I easily downgrade a desktop to a server"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by bdk6m2007 on 2007-11-07
I have a machine that was installed as a Ubuntu 7.10 Desktop but I really need it to be a server.  Is there an easy way (via apt-get??) to downgrade from a desktop to a server?  I don't want all the packages associated with the desktop.  I tried removing just the ubuntu-desktop package but that just removed itself, not all of its dependencies like I was hoping.  Any ideas?

Is the path of least resistance really just to re-install from the server CD?

---

### Post by HermanAB on 2007-11-07
Linux is Linux is Linux...  there is no real difference between a server and a desktop.

The Linux scheduler is very good.  If you have X running, then it will be swapped out when another process needs the memory, so you need not worry about it, but you could also quit X with "init 3".

Cheers,

Herman

---

### Post by g2g591 on 2007-11-07
id say try sudo apt-get autoremove, which will remove any autoinstalled packages (dependances) that were installed with a previously installed packages that were removed. and to install the server packages try sudo apt-get install ubuntu-server

---

### Post by bdk6m2007 on 2007-11-07
I did try autoremove but it didn't do anything unfortunately.  I don't want all of the desktop packages because this is supposed to be a build server and I don't want extra stuff available for builds to link against.  It's looking more and more like a re-install is in the stars.  :-(

---

### Post by g2g591 on 2007-11-07
if you really want to remove the gui (like a server install) use sudo apt-get remove xserver-xorg . this will remove the program the provides graphics (and everything that depends on it, like gnome and most common programs) and will leave you with a terminal.

---

### Post by bdk6m2007 on 2007-11-07
OK I figured out a way to do it, thanks for all the suggestions.  The number of packages removed (651) was astonishing!  Here's what I did:[LIST=1]
[*]on another identical already installed server:[/LIST]```

dpkg --get-selections > package_list.txt
scp package_list.txt adminuser@<IP of new box>:~

```
back on the new machine logged in as adminuser (user created during installation)
```

sudo dpkg --clear-selections
sudo dpkg --set-selections < package_list.txt
sudo apt-get update
sudo apt-get -u dselect-upgrade
sudo dpkg-reconfigure locales

```
A bit painful and required another existing and nearly identical machine but it worked.  The locales reconfigure was necessary because somehow locales got hosed (not sure why).  When I removed  X as suggested it actually didn't remove gdm and gnome as expected but this did the trick.

---

