---
title: "Installing Wesnoth... how do I upgrade it?"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-26
High, as I'm typing this, I'm installing Wesnoth from the Synaptic Package Manager.
I noticed that in the manager the version is older than the one on the game website.
Once installed, is it possible to just upgrade it??? How? 

does the apt-get upgrade command upgrade all the software installed?

---

### Post by KingBahamut on 2005-08-26
Where there are updates on the repositories that are newer than your installed versions. 

If you want a newer version, and dont want to recompile from source, issue a request over in the backports forum for an update release. 

You could possibly search debians main repo, and find a deb there for the current release. 

A search there bred this link 
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wesnoth](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wesnoth)

You can try to install one of those binaries and it might work , but no promises.

---

### Post by ROUBOS on 2005-08-26
So downloading a .dep file and installing it (what's the command) autonaticaly updates the game/program???
No need to uninstall and install new version???

---

### Post by KingBahamut on 2005-08-26
Roubos, if you use Synaptic, Automatic Updater thingy, or apt-get upgrade all , youll upgrade all packages on your system for which new ones exist. 

if you want a package that isnt on the repo then youll have to grab source or a binary and install it yourself. 

with respect to a deb file , 

sudo dkpg-i nameofpackage.deb 

be careful though, using untested debs can cause apt-get and dpkg to act a little weird, specially where dpkg is concerned and there are unmet dependencies, so be careful there.

---

### Post by ROUBOS on 2005-08-26
I guess since I'm still a noob, I should stick to the Synaptic Package Manager

---

### Post by matthew on 2005-08-26
[QUOTE=ROUBOS]I guess since I'm still a noob, I should stick to the Synaptic Package Manager[/QUOTE]
Wise choice for now.

---

