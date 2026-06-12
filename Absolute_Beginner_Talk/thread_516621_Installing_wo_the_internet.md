---
title: "Installing w/o the internet"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by .feint on 2007-08-03
I am dual booting Vista and Ubuntu-FF.

I do not have a net connection for Ubuntu because I am on wireless, and I cannot do sudo apt-get, so please don't tell me to do that ;)

I need to know how to install things without the internet.  I can download stuff when in Vista, but idk how to install under Ubuntu.

This is all to get my internet working in the first place, but I have an idea of how to do it, I just don't understand how to install say, unshield, without the net. 

Thanks.

---

### Post by Ice_Dragon on 2007-08-03
You can manually download whatever packages you need from here.  Transfer them onto Ubuntu and  double-click to install them.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by .feint on 2007-08-03
Rofl, thanks.

Holy idiot (me I mean.)

---

### Post by Majorix on 2007-08-03
If your wireless works under Windows and not under Ubuntu, you could use a tool called ndiswrapper to install the windows wireless drivers under Ubuntu. Then you can use internet with Ubuntu too.
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

---

### Post by .feint on 2007-08-03
I know, but I need to install unshield, and using the .tar.gz thing doesn't work when I double click it.

---

### Post by ugm6hr on 2007-08-03
This thread ([http://ubuntuforums.org/showthread.php?t=512364](http://ubuntuforums.org/showthread.php?t=512364)) gives details on how to automate the install procedure - although if this is only for a few .debs - getting them manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) works well.

If you have problems with dependencies - just copy all the .debs to var/cache/apt/archives and install from Synaptic.

---

### Post by Hospadar on 2007-08-03
If you are using open source drivers to get your wireless working, I suspect that you are probably getting the source and you need to build it.  You should manually download build-essential and it's dependancies and install them so that you can build source packages if that is the case.

---

