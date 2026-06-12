---
title: "Error installing Envy"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by UbunduNoob on 2007-04-01
Hi.  I'm really new to Ununtu.  I don't think that they system is running on the current Nvidia drivers. I've been reading multiple forums as how to fix this and so far it looks like Envy is the way to go.  When trying to install the .bin package installer says "Error: Dependency is not satisfiabe: build-essential"  

I would like to get this going.  Please help. Thank you.

---

### Post by Perfect Storm on 2007-04-01
```
sudo aptitude install build-essential
```

Or you can install the drivers manually (good way to learn).

---

### Post by Dual Cortex on 2007-04-01
sudo apt-get build essential should take care of it. Although I think envy installs them by default. Anyway what version are you using?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

[envy_0.9.1-0ubuntu4_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb")

Ripped from the site (and modded to your needs):

1) Remove the older version of envy (you can skip this step if you only used the Nvidia installer):sudo aptitude purge envy
> sudo aptitude purge envy

2) Download and install the deb package:

double click on the deb package in Ubuntu (or Xubuntu) or right click on the deb package and select "Kubuntu Menu/install"

3) Make sure that all the dependencies were installed by typing:
> sudo apt-get install -f

4) Launch Envy's GUI (inside a Desktop Environment such as GNOME,KDE, etc.) by selecting it in the "Applications/System Tools" menu

Then simply select "*install the NVIDIA driver*" and click "*Apply*"

---

### Post by Maestro23 on 2007-04-01
Some Useful links for ya also:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by UbunduNoob on 2007-04-01
Thanks.  that extra info helped a lot!

---

### Post by Maestro23 on 2007-04-01
> **UbunduNoob said:**
> Thanks.  When I did that it said "Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed."

So I downloaded build-essential and tried to install it and it said Error: Dependency is not satisfiable: libc-dev.  I downloaded that and it said "more recent version installed.

Okay, so I'm guessing trying to install from the desktop is my problem.

Do I have to move the .bin files to another file directory before trying to install them? :confused:

You need to enable extra repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Do that and try again.

---

### Post by Dual Cortex on 2007-04-01
nvm

---

