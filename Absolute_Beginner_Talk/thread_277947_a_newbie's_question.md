---
title: "a newbie's question"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by yuliang on 2006-10-15
What are the differences between 'update' and 'upgrade'?

---

### Post by Klaidas on 2006-10-15
Update - install a path/fix/etc... Ex: I installed an update for Firefox, now a bug is fixed
Upgrade - well, umm... a BIG update? :D Ex: I upgraded my Ubuntu 6.06 to 6.10, now everything is broken :D

---

### Post by ciscosurfer on 2006-10-15
When you change your repository list, in order for them to take effect, it is necessary to issue the 'update' command prior to issuing 'upgrade' or 'dist-upgrade' like so```
sudo aptitude update
sudo aptitude upgrade
```or```
sudo aptitude update
sudo aptitude dist-upgrade
```In my opinion, it's always a good idea, if you want to stay completely up-to-date, to issue the latter commands, update...dist-upgrade.

---

### Post by Neocyb on 2006-10-15
just a stab in the dark (correct me if I'm wrong) :

Update : software related
Upgrade : Hardware related

So for instance I'm going to update my version of Ubunto from 5.xx to 6.xx

and I'm going to upgrade my P3 to P4

(guess I was wrong):???:

---

### Post by aysiu on 2006-10-15
```
sudo aptitude update
``` fetches the list of installable software ```
sudo aptitude upgrade
``` gets the newest available versions of the programs you already have installed ```
sudo aptitude dist-upgrade
``` gets the latest collective package of what should be installed for Ubuntu *and* upgrades to the newest available version the applications you already have installed.

---

### Post by Dinerty on 2006-10-15
updates = Just little bug fixes,improvements, something like upgrading Opera 9.01 to 9.02

upgrades = Something quite big like a dist upgrade from dapper drake to Edgy eft 6.06 to 6.10

---

### Post by PriceChild on 2006-10-15
In a clearer form to what aysiu posted...

update grabs a list of all the available packages.

upgrade gets the latest versions of your installed packages and installs them WITHOUT installing new packages.

dist-upgrade gets the latest versions of your installed packages and installs them installing new packages if necessary in order to satisfy dependencies.

---

### Post by yuliang on 2006-10-16
I agree that 'upgrade' updates packages already installed in the system. But obviously 'update' will not install all available packages. I am still confused about what the command 'update' actually does.

---

### Post by ciscosurfer on 2006-10-16
> **yuliang said:**
> I agree that 'upgrade' updates packages already installed in the system. But obviously 'update' will not install all available packages. I am still confused about what the command 'update' actually does.

I answered this question in my first post:

> **ciscosurfer said:**
> *When you change your repository list, in order for them to take effect, it is necessary to issue the '**update**' command prior to issuing 'upgrade' or 'dist-upgrade' like so*```
sudo aptitude update
sudo aptitude upgrade
```or```
sudo aptitude update
sudo aptitude dist-upgrade
```In my opinion, it's always a good idea, if you want to stay completely up-to-date, to issue the latter commands, update...dist-upgrade.

---

### Post by PriceChild on 2006-10-16
Update gets your computer to speak with the servers, and find the latest lists for each repository about what software and which versions are availiable.

---

### Post by ciscosurfer on 2006-10-17
> **PriceChild said:**
> Update gets your computer to speak with the servers, and find the latest lists for each repository about what software and which versions are availiable.

Negative.  Well, sort of.  I know what you mean, but I think the OP will find the various information we've previously listed to be confusing.  Below is from the man pages (and what I've already mentioned in my 1st and 2nd posts.)  Type **man apt-get** into a terminal to find out more.

**update** update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the location(s) specified in */etc/apt/sources.list*. For example, when using a Debian archive, this command retrieves and scans the *Packages.gz* files, so that information about new and updated packages is available. An update should always be performed before an upgrade or dist-upgrade. Please be aware that the overall progress meter will be incorrect as the size of the package files cannot be known in advance. [B]

upgrade[/B] upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in */etc/apt/sources.list*. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be performed first so that **apt-get** knows that new versions of packages are available. [B]

dselect-upgrade[/B] dselect-upgrade is used in conjunction with the traditional Debian packaging front-end, **dselect**(number eight, not a smily face). dselect-upgrade follows the changes made by **dselect**(number eight, not a smily face) to the Status field of available packages, and performs the actions necessary to realize that state (for instance, the removal of old and the installation of new packages). [B]

dist-upgrade[/B] dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; **apt-get** has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The */etc/apt/sources.list* file contains a list of locations from which to retrieve desired package files. See also **[apt_preferences]("http://www.die.net/doc/linux/man/man5/apt_preferences.5.html")**(5) for a mechanism for overriding the general settings for individual packages.

---

