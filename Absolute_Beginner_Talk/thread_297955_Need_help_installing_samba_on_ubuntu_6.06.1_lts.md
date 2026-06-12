---
title: "Need help installing samba on ubuntu 6.06.1 lts"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by slafco on 2006-11-12
Ok, I have been trying to install samba, following this guide, [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) . When I type in the command sudo apt-get install samba in the terminal, it comes up with this.

sgavriloski@slafco-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate

I checked the etc/init.d/ directory and there is no file named samba.

Does anyone know hot to fix this? Do I have to download and install a samba package. (I am using Ubuntu 6.06.1 LTS by the way).

Any help would be greatly appreciated, I need to get this working urgently.

---

### Post by jordanmthomas on 2006-11-12
```
sudo apt-get install smbclient samba-common
```
since they replace the samba server.

Also, to see all the samba packages, try 
```
apt-cache search samba
```
I don't use Ubuntu, so I can't give you any exact package names...sorry about that.

---

### Post by jcrochford on 2006-11-12
slafco,

This may seem to be too much of a long-distance workaround, but if you're using the Gnome Desktop environment and you're trying to install Samba, you can do so by installing the KDE.  I installed the official modules via the Synaptic Package Manager by installing 'KDE' and not 'Kubuntu', although the 'Kubuntu' install likely has it, as well.  When I switch to the KDE, I can easily access Samba by selecting it from the KDE menu.  You could likely set it up to work from within Gnome at that point, as well.  The only problem I've had with Samba has been mounting remote folders.  My Ubuntu laptop sees my Windows desktop, they're just not communicating properly.  I'm sure I'll figure it out in the next day or so.  By brother has not problems, though.  Good luck.

---

### Post by slafco on 2006-11-12
Thanks guys, I just downloaded an installation for the package and followed the guide and I have managed to get it working 100% now :mrgreen: 

Thanks for the help!

---

