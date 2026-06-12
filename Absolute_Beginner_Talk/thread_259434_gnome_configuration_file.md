---
title: "gnome configuration file"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by mikl2 on 2006-09-17
Very new to Linux (Ubuntu).  Installed Ubuntu 5 days ago and trying to learn. I can get my way around WindowsXP pretty good, but wanted to jump on the Linux bandwagon.  I like to keep my XP machine clean and lean.  I install many applications to try out, and find that I don't like them and uninstall them.  In XP that usually leaves the registry bloated with left over entries.  I assumed Ubuntu would not do that.  I installed (Synaptic) "Brightside" and decided I didn't want it so uninstalled (Synaptic).  So to check how thorough the uninstall went, I hit Alt-F2 and typed in 'gconf-editor' and hit enter to see it.  There is an "Brightside" enty.  Should that have been removed?  How can I keep my Ubuntu install lean and clean?

---

### Post by bulldog on 2006-09-17
When you want all the dependency's removed when you uninstall an application,use aptitude to install on the first place.

sudo aptitude install appsname
sudo aptitude remove appsname

This will clear all the dependency's which came with the app.

But there's no need to be worried about an entry in gconf-editor.
It has no effect on your system.

You could also do 

sudo aptitude autoclean to remove older packages which are no longer of use.

Take a good look in synaptic and his options you could be suprised.

---

### Post by mikl2 on 2006-09-17
Thank you for the quick response.  So.....are you saying it's best to install/uninstall ALL apps with aptitude rather than synaptic?  If so, what are the advantages to using synaptic?

---

### Post by mikl2 on 2006-09-17
I found my answer here:
he advantages of aptitude over apt-get
aptitude has an important feature that its command-line cousin apt-get and the graphical frontends Synaptic and Adept do not have--it remembers dependencies. If you update with aptitude, install with aptitude, and then uninstall with aptitude, all the dependencies you installed with a particular package will be removed when that package is removed (unless other packages also depend on those dependencies). If you install with Synaptic, Adept, or apt-get, uninstalling will uninstall only the package you specify--not the dependencies that came with it.

For example, if you install kword, you will also install kspread, kword-data, and libwv2-1c2. If you install kword with aptitude and then uninstall with aptitude, kspread, kword-data, and libwv2-1c2 will also be removed along with kword. If, however, you install kword with apt-get and then uninstall kword, kspread, kword-data, and libwv2-1c2 will remain installed, and you will not be prompted to remove them.

Thanks

---

