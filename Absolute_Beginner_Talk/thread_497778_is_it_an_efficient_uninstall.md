---
title: "is it an efficient uninstall?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-07-10
When we use apt-get to remove a package, does apt-get really remove every file of the package or is it prone to leaving a few left overs lying here and there like it happens sometimes in windows.

what is the difference between dpkg and apt-get? They pretty much do the same things.

---

### Post by Nekiruhs on 2007-07-10
The only files it leaves behind are dependencies and configuration files.
To remove configuration files ```
sudo apt-get remove --purge programname
``` To remove unessecary dependencies type ```
sudo apt-get autoremove
```
dpkg handles the installation of .debs while apt-get retrives and passes them to dpkg.

---

### Post by wpshooter on 2007-07-10
Use Synaptic package manager.

---

### Post by Nekiruhs on 2007-07-10
> **wpshooter said:**
> Use Synaptic package manager.
Synaptic is just a front-end to apt-get. It still doesn't remove with out the above steps unless you mark for complete removal.

---

### Post by KIAaze on 2007-07-10
Previously it was recommended to use aptitude instead of apt-get to keep the system cleaner, but this doesn't seem to be the case anymore:
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

But with aptitude, it will remove all dependencies by default when you use "aptitude remove".
With apt-get, you'll need to use the previously suggested commands.

---

### Post by wpshooter on 2007-07-11
> **Nekiruhs said:**
> Synaptic is just a front-end to apt-get. It still doesn't remove with out the above steps unless you mark for complete removal.

It's on the menu, all you have to do is check it.

---

### Post by PartisanEntity on 2007-07-11
Here is a useful article on how to clean up your system:
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by az on 2007-07-11
> **Nekiruhs said:**
> The only files it leaves behind are dependencies and configuration files.
To remove configuration files ```
sudo apt-get remove --purge programname
``` To remove unessecary dependencies type ```
sudo apt-get autoremove
```
dpkg handles the installation of .debs while apt-get retrives and passes them to dpkg.

--purge will remove the deb package configuration, but it will not remove the application's configuration.  Debconf is a database with all the packages configurations.  In Ubuntu, the default is usually taken and we don't get asked a lot of questions like in Debian.  Debconf is not the same thing as the applications' runtime configuration.

For example, if you install apache2, it will create an apache2 directory in /etc.  That directory will not be removed when you remove the apache2 packages.  Similarily, when a desktop application is run, it will create a configuration file or directory in your home directory (.mozilla, for example)  The package manager does not touch your home drive.  Users need to delete them themselves.

Some apps also create stuff in /var/lib.  


> **desijays said:**
> 
what is the difference between dpkg and apt-get? They pretty much do the same things.

Dpkg is the lowest-level package tool in the toolchain.  All ubuntu package managers will end up running dpkg to install individual packages.  Apt handles packages from repositories, resolving dependencies.  If you try to install a deb by hand and the dependency is not satisfied, it will just not install it.  You would have to tell dpkg to install that package and the other packages that are needed all together for them to be installed.  Using apt, you just specify the package and if all the dependencies are available in the repos that apt knows about, apt will tell dpkg to install all those packages.  Synaptic or Add-Remove programs are frontends to Apt.

---

