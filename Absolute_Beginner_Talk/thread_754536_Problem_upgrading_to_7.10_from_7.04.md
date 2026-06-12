---
title: "Problem upgrading to 7.10 from 7.04"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by MasterCylinder on 2008-04-13
So I am trying to upgrade to Gutsy (7.10) and when ever I try to 

 System> Administration> Update Manager> 'New Distribution' Upgrade

I get these error messages after a little bit I get the following errors:

[PHP]Failed to fetch http://repository.debunutu.org/dists/feisty/Release.gpg Could not resolve 'repository.debunutu.org'
Failed to fetch http://repository.debunutu.org/dists/feisty/multiverse/i18n/Translation-en_US.bz2 Could not resolve 'repository.debunutu.org'
Failed to fetch http://repository.debunutu.org/dists/feisty/multiverse/binary-i386/Packages.gz Could not resolve 'repository.debunutu.org'
[/PHP]

[IMG]http://i266.photobucket.com/albums/ii263/Tehubergethkill3r/Screenshot.png?t=1208139696[/IMG]



Thanks in advance

---

### Post by Oldsoldier2003 on 2008-04-13
make sure you have ubuntu-desktop installed and upgrade all your installed packages before trying to upgrade.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
```

then try the dist upgrade

---

### Post by MasterCylinder on 2008-04-14
Im still having problems, even after I ran the commands you told me to try...

When I try to update I get the following message > Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

when i do run 

> sudo apt-get install -f 

something about Pidgin pops up

> mcmanus@mcmanus-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gaim
Suggested packages:
  libmeanwhile1 libzephyr3 tcl8.4 tk8.4
The following NEW packages will be installed:
  gaim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/1741kB of archives.
After unpacking 4923kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 106539 files and directories currently installed.)
Unpacking gaim (from .../gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package pidgin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mcmanus@mcmanus-desktop:~$ 


---

### Post by Pijits_1 on 2008-04-14
When I upgraded I just downloaded the newest CD and popped it in like a fresh install (was my original intent) but discovered that it can take all home directories and keep all files on the system.

So all you do is download the ISO of the latest version (might as well wait until 8.04 comes out in like two weeks now lol)

Burn to disk

Pop in and go through install

Get prompted to keep files from your home directory

Watch the update complete.

Warning this may get rid of some programs that you may have, I'm not to sure, try to use this method as more or less a last resort if using the update manager doesn't work.

---

### Post by MasterCylinder on 2008-04-14
Thankyou for the advice and help. Your probably right, I will jsut wait for the new distro and do it that way. But anyway thanks again :)

---

