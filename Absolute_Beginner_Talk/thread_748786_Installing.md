---
title: "Installing"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by PFSpectrum on 2008-04-07
Ok im just starting in Ubuntu and installing software is hard... there are all these commands like sudo, and apt-get and all this stuff and i don't know what this means... Is there a guide somewhere on the internet that teaches the basics of these commands and how to install software with them. I don't want a guide on how to install a certain software i want to know how to install files when i find them.. without having to read a read me... i just wanna know how to install things easier...

---

### Post by webhog on 2008-04-07
I think apt-get is the greatest tool there is...
General basic usage:

apt-get update                --> will update the package lists you have
apt-get upgrade              --> will download and install any upgraded packages for the programs you have installed

apt-get install packagename        --> will download and install a pre-built package for a program (Check out the package lists for the package names of programs, since you have to type the package name exactly for it to work.  For example.  If you want to install lynx, the package name might be lynx2.0.2 or something like that).  If you download the packaged file from the internet (i.e. lynx.deb), you can install it with the dpkg command (dpkg -i file.deb).

apt-get uninstall  packagename   --> will remove a package
dpkg -P packagename  --> will purge old configuration files, is useful.



Check this wiki out, it should help you out (Ubuntu is very similar to debian, so you should be ok reading this):

[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

---

### Post by PFSpectrum on 2008-04-07
thank you.. things are making a little more sense now lol =]

---

### Post by wolfen69 on 2008-04-07
here is a good link [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) and this [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by lackofcreativity on 2008-04-07
You should only really use the terminal to install things if you know the exact package name and what it does. Otherwise, use Applications -> Add/Remove... to install things or if they're not there, System -> Administration -> Synaptic Package Manager. Just a thought.

---

