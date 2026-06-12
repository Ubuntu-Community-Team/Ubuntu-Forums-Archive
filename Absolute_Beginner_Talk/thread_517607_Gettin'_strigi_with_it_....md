---
title: "Gettin' strigi with it ..."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-08-04
My update manager shows me that there is an update for strigi-daemon, but the update is blanked out, I can't tick it and therefore can't download & install the update.  That doesn't make sense and has never happened to me before.
Synaptic shows me as well that there is an update for strigi-daemon, but sho' nuff, when I tell it to install the update it comes back at me with this:  "depends on dbus-x11, but is not installable".
And when I tell Synaptic to search for dbus-x11 it doesn't return any results.
I'm using Xubuntu and have both the Gnome and KDE runtimes loaded at startup.
So what's going on here?  Why can't I install the update to strigi-daemon?  And what's dbus-x11?

---

### Post by Blofeld on 2007-08-04
Hm, dbus "allows different programs to communicate with each other" ... I'm still unclued.

---

### Post by Ubuntiac on 2007-09-28
I can't guarantee this will help, but I've found what often has helped me when I've had various "Can't install because of..." kind of errors is just cycling through the following lines below a couple of times in the terminal:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get -f install
sudo apt-get install <<INSERT NAME OF PACKAGE YOU WANT HERE>>

The first one tries to configure  packages that were downloaded but not installed yet (which can happen sometimes if they were set to install after something that failed).

The second one updates your list of packages to make sure you're downloading the latest.

The third one tries to install dependencies needed for packages yet to be installed.

The fourth one says "Hey install my package... Now that I've hopefully cleared up the problem in the first three steps."

Sometimes (especially, if you're on a development version and haven't upgraded packages in a while) you may need to cycle through a couple of times as fixing one problem, then lets it fix another bunch and so on.

Hope this helps!

PS Oh and for anyone more technically inclined, writhing in your seat at how many things were incorrect in this last post, please feel free to jump in and correct me. :)

---

