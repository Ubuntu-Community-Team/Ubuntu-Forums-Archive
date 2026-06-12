---
title: "Can't install at ALL."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by dragonchilde on 2007-02-20
I'm about at my wit's end. I've been proceeding very slowly, wanting to take this one step at a time, but now it appears that I just plain CAN'T install this on this PC. 

I'm running a Nvidia geForce4 MX 400, and the PC will NOT load the GUI. It's refusing.  

I know both CDs work (I've tried both dapper and edgy) because I got them to load on this, my main PC.  

The whole thing loads just fine, until it tries to load a GUI, then I get all kinds of problems.  If I use the onboard card, I get a no screen found error.  IF I switch to the onboard card, that's where things go badly wrong.  It pulls up some kind of error message (too quickly for me to read) then starts filling the screen with "User not known to the underlying authentication module" and then crashes. This same PC will boot XP just fine.

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) - I was going to try this, but I have to actually be able to install Ubuntu first. I may be able to install it using this PC, but that will take away all of my online documentation, so I'll be flying blind. 

I'm about to try that now, but I have a sinking suspicion that just plain won't work.  Never know until you try. 

Please, has anyone got ANY help for me? I'm normally a pretty patient soul, but this is really starting to get to me.

---

### Post by taurus on 2007-02-20
Try the alternate CD.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by dragonchilde on 2007-02-20
Okay, I managed to get it installed using this PC; will the alternate CD help me manage the problems and configure the HD for the other PC?

---

### Post by Tomosaur on 2007-02-20
The alternate cd will provide you with a command line installation of Ubuntu. Once you're all installed - reboot the machine, log in via the command line, and use the following commands to (hopefully) get the GUI working:
```

sudo aptitude install ubuntu-desktop
sudo aptitude install nvidia-glx-legacy

```
The first command will take a while - it downloads all of the desktop packages.
The second command downloads the legacy nvidia drivers, which should hopefully allow you to  get the GUI running.

You may want to substitute ubuntu-desktop for xubuntu-desktop. Xubuntu uses XFCE, which is more suitable for older hardware. Instead of the first command, use:
```

sudo aptitude install xubuntu-desktop

```
instead.

Good luck :)

---

