---
title: "dpkg is broken and i need help"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Countra on 2008-01-17
Okay so, the dpkg is broken and when i try to do [Edit > Fix broken packages] is get:
> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

And when i try to fix it through the terminal(or atleast i think i am trying to fix it. lol), i get this:
> arsham@arsham-desktop:~$ sudo dpkg --configure -a
[sudo] password for arsham:
dpkg: status database area is locked by another process

are there any additional details or anything i should give? And btw, this is the only broken package i have.

---

### Post by Dr Small on 2008-01-17
Close Synaptic and try running the command again.

---

### Post by Countra on 2008-01-17
well, nothing happens. At all. Now how weird is not that.. lol, well you seem to be interested in sherlock holmes and all and this seems to be a mystery so.. would you mind? xD

> root@arsham-desktop:/home/arsham# dpkg --configure -a
root@arsham-desktop:/home/arsham# 


---

### Post by maybeway36 on 2008-01-17
Seems like reboting might help. I don't know what else to do, myself.

---

### Post by Countra on 2008-01-18
rebooting did not help. Btw, im trying to install the zd1211 driver, that is my prime objective but to be able to do that i first have to fix this broken package. Would removing it and reinstalling it be a good idea?

EDIT: btw, the dpkg package goes broken every time i select zd1211 for installation so the to does not seem  to be very good friends. Or something like that.

---

### Post by Countra on 2008-01-18
bump

---

### Post by Dr Small on 2008-01-18
Forget that.
Just try running:
```
apt-get -f
```

---

### Post by philinux on 2008-01-18
dont forget to put in 

sudo

first

---

### Post by Sef on 2008-01-18
Try this first:

```
sudo dpkg --configure -a
```

then if it doesn't work, then try this:

```
sudo apt-get -f
```

---

### Post by Countra on 2008-01-18
Well, thanks for all the responses but here is what i got from doing the "dpkg --configure -a" and "apt-get -f"
> arsham@arsham-desktop:~$ sudo dpkg --configure -a
[sudo] password for arsham:
arsham@arsham-desktop:~$ sudo apt-get -f
apt 0.7.6ubuntu14 for i386 compiled on Oct 15 2007 20:39:10
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.


Also, here is another thing i tried:
> root@arsham-desktop:/home/arsham# apt-get install dpkg -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
The following packages were automatically installed and are no longer required:
  libtwolame0 libsvga1 libboost-thread1.34.1 libboost-date-time1.34.1
  classpath-gtkpeer libdvdnav4 classpath-common gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.

And oh yeah, as i said; the dpkg shows up as 'broken' only when i select the zd1211 for installation.

---

### Post by az on 2008-01-18
That should be

sudo apt-get -f install


And where did you get the package for the zd1211?

An improperly built package can break the package manager.  I suggest you stay away from non-official packages.  Is this the case?

---

### Post by Countra on 2008-01-18
zd1211 is a driver which came in the cd for the WiFi MAX. (yep, they put drivers for linux to in the cd! yahoo xD) so it is as official as it can get.
And that sudo apt-get -f install:
> root@arsham-desktop:/home/arsham# apt-get -f install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.


So it didnt solve the problem but thanks anyways, now maybie we can take away the focus from "sudo apt-get -f install" since it didnt do anything hehe.

And btw i have never had any problems with non-official packages, more so infact with the "official" ones(like right now with the dpkg for example lol xD)

---

### Post by az on 2008-01-18
Not 

sudo apt-get -f install dpkg

but

sudo apt-get -f install

That will reveal what problems the package manager is having.  That's the place to start.

And no, just because a package is on a cd does not make it official.  It generally makes it outdated.  It's no guarantee it will work.  Use the repositories.

---

### Post by Countra on 2008-01-18
This was what i got:
> root@arsham-desktop:/home/arsham# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.
root@arsham-desktop:/home/arsham# 
repositories? You mean the packages in the package manager, right?

---

### Post by Countra on 2008-01-19
bump

---

### Post by az on 2008-01-20
> **Countra said:**
> This was what i got:


So what's the problem?  Dpkg is not broken.

---

### Post by Countra on 2008-01-20
Well, it seems like that, yes. However, in the synaptic package manager; when i tried to 
install a certain package, 'dpkg' showed up as broken. But the problem might have been on my behalf i must say and i have now founded a better package. =)
So i would say that the thread is rather solved... Or maybie not. lol.

---

### Post by az on 2008-01-20
> **Countra said:**
> Well, it seems like that, yes. However, in the synaptic package manager; when i tried to 
install a certain package, 'dpkg' showed up as broken. But the problem might have been on my behalf i must say and i have now founded a better package. =)
So i would say that the thread is rather solved... Or maybie not. lol.

I suggest that the package that you wanted to install was not properly built.

---

