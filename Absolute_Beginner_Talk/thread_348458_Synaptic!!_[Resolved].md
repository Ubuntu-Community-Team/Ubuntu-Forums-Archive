---
title: "Synaptic!! [Resolved]"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-28
ok, my synaptic package manager is not working, it says all of my installs are not working, please help....i have no idea wut to do.....and i just found out which programs to get from it...any help appreciated

---

### Post by BarfBag on 2007-01-28
Give us more details.  What error is it giving you?

---

### Post by taurus on 2007-01-28
What happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by Sniper99 on 2007-01-28
spencer@spencer-desktop:~$ sudo aptitude update
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:8 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/free Packages
  404 Not Found
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release

Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:11 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release [745B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/non-free Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Fetched 945B in 3s (310B/s)
W: GPG error: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by taurus on 2007-01-28
Did you have synaptic open or something running in the background?

```
ps -A
```

---

### Post by sloggerkhan on 2007-01-28
Sometimes this happens if you have stuff installing on another terminal.

---

### Post by Sniper99 on 2007-01-28
yeah i think i did, is that a problem

---

### Post by taurus on 2007-01-28
You cannot have synaptic and apt-get/aptitude running at the same time.  If you want to run apt-get/aptitude from a terminal, you need to shutdown synaptic first.

---

### Post by Sniper99 on 2007-01-28
i didn't have apt get running at the time that i was trying to use synaptic....and it just had error messages, after it was basically done installing the packages

---

### Post by taurus on 2007-01-28
So synaptic is closed now!  Run that command again to see exactly what's the problem is.

```
sudo aptitude update
```

---

### Post by Sniper99 on 2007-01-28
spencer@spencer-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:9 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:10 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg [191B]
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:11 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release [745B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/non-free Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) 6.06-plf/non-free Packages
  404 Not Found
Fetched 945B in 4s (198B/s)
Reading package lists... Done
W: GPG error: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

---

### Post by taurus on 2007-01-28
I would either remove those two repos or at least put a # sign in front of them in /etc/apt/sources.list to comment them out.

```
gksudo gedit /etc/apt/sources.list
```

```

#deb http://wine.lowvoice.nl
#deb http://packages.freecontrib.org

```
Save the changes and run that command again.

```
sudo aptitude update
```

---

### Post by Sniper99 on 2007-01-28
ok that was sort of confusing, so i run the first command, then the second, and then the third one, or do i run the first, and the second will pop up, and then run the third

---

### Post by taurus on 2007-01-28
You edit /etc/apt/sources.list with this command.

```
gksudo gedit /etc/apt/sources.list
```
Then, scroll down the list and put a # in front of those two repos.  Save the changes and run the last command again.

```
sudo aptitude update
```

---

### Post by Sniper99 on 2007-01-28
ok, this is what came up......from what i can understand it worked.......


spencer@spencer-desktop:~$ gksudo gedit /etc/apt/sources.list
GTK Accessibility Module initialized

(gedit:20828): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
spencer@spencer-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 9B in 1s (5B/s)
Reading package lists... Done

---

### Post by taurus on 2007-01-28
Now, see if there are any updates with

```
sudo aptitude upgrade
```

---

### Post by Sniper99 on 2007-01-28
ok, the updates were the ones that i failed to install in the update manager becuase it was failing also.....this is wut came up


spencer@spencer-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  firefox firefox-gnome-support
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7944kB/8020kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 [7944kB]
Fetched 4677kB in 1m12s (64.4kB/s)
(Reading database ... 118944 files and directories currently installed.)
Preparing to replace firefox-gnome-support 1.5.dfsg+1.5.0.9-0ubuntu0.6.06 (using .../firefox-gnome-support_1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06 (using .../firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb) ...
Unpacking replacement firefox ...
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Setting up firefox (1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1) ...

Setting up firefox-gnome-support (1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1) ...

Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
spencer@spencer-desktop:~$

---

### Post by taurus on 2007-01-28
Were you trying to install an antivirus, clamav?  Try these.

```
sudo aptitude purge clamav-base
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Sniper99 on 2007-01-28
this is very confusing i don't remember ever installing clamav, i did do firestarter


spencer@spencer-desktop:~$ sudo aptitude purge clamav-base
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  clamav-base{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 401kB will be freed.
Do you want to continue? [Y/n/?] y

Size changes will be shown.

The following packages will be REMOVED:
  clamav-base{p} <-401kB>
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 401kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 118942 files and directories currently installed.)
Removing clamav-base ...
Purging configuration files for clamav-base ...
groupdel: group clamav does not exist

---

### Post by taurus on 2007-01-28
Now, run the last two commands to see if you can updates your machine.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Sniper99 on 2007-01-28
does that mean that automatix is messed up?


spencer@spencer-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [8412B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Get:11 [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages [528B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Fetched 9137B in 2s (3148B/s)
Reading package lists... Done
spencer@spencer-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  automatix2
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 181kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main automatix2 1.1-2.9-6.06dapper_i386 [181kB]
Fetched 181kB in 3s (53.6kB/s)
(Reading database ... 118925 files and directories currently installed.)
Preparing to replace automatix2 1.1-2.8-6.06dapper_i386 (using .../automatix2_1.1-2.9-6.06dapper%5fi386_i386.deb) ...
Unpacking replacement automatix2 ...
Setting up automatix2 (1.1-2.9-6.06dapper_i386) ...

---

### Post by taurus on 2007-01-28
Not really.  Automatix2 has a new version and it's upgraded your machine to the latest version.  Looks like everything is back to normal for your machine now.

---

### Post by Sniper99 on 2007-01-28
thank you so much taurus, you really helped me, and i sort of understand this, just a tad....thanks again....

---

### Post by taurus on 2007-01-28
You're welcome.  To summarize what we did so you would understand a little better.  You couldn't use synaptic/apt-get/aptitude because you had a couple of dead repos and a dead package.  So, we edited /etc/apt/sources.list and commented out those two repos and removed the dead package.  

Now, the Sun is out and everybody is happy again.  :wink: 

Good luck and have fun with Ubuntu.

---

