---
title: "Failed Install"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by teotwawki on 2007-07-20
I've screwed up my Package Manager DB somehow, trying to install VirtualBox. No matter whether I try to use Synaptic or Add/Remove or apt-get as root, the install fails.

Synaptic Output:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Program then exits

Add/Remove:

Can't Add/Remove anything. Have tried various packages (games) as well as VMWare Player and the program hangs.

apt-get from within a Terminal:

$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

I've rm'ed all in /tmp and the .deb files for VBox. What next?

Thx...

---

### Post by geist27 on 2007-07-20
Doh! That sounds strange, have you tried:

```
$ sudo apt-get update
``````
$ sudo apt-get upgrade
```When I get a nice new vanilla install of ubuntu after setting up my display drivers with 

**Envy** [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

the very next thing I do is run 

**Automatix** [http://www.getautomatix.com]("http://www.getautomatix.com/")

Automatix sets up a ton of stuff including windows codecs as well as virtualbox

---

