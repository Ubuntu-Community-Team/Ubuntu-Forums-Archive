---
title: "Package Management 101"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-08-01
After having used Ubuntu and Debian for a real long time, and almost entirely through the command line, I thought I would post a quick reference of sorts for all package management related tools in one place .

I would definitely like to have community support for improving this, and am sure it will be helpful for all terminal junkies. 

1. Listing of repositories
-- Found at /etc/apt/sources.list
-- Lines starting with # indicates comment
-- Lines starting with deb indicate pre-packaged binaries
-- Lines starting with deb-src indicate source. Can be commented for most users

2. Package management tools
-- aptitude
-- dpkg
-- apt-cache

3. Updating index of repositories
```
sudo aptitude update
```

4. Searching for a package from the repos
```

aptitude search package-name
apt-cache search package-name
apt-cache search --names-only package-name

```

5. Listing all installed packages
```
dpkg --list | grep ^ii
```
You can further pipe it using grep to search for a installed package that matches some name
```
dpkg --list | grep ^ii | grep package_name
```

6. Install a .deb file you downloaded from the internet
```
sudo dpkg --install path_to_file_name
```
This is not always advised. First check with the package documentation if you have required dependancies, and it is always better to install from the repositories. 

7. Install a package repo
If you know the package name, or if you know the package exists after a search as per 4 above, 
```
sudo aptitude install package-name
```
This will pull all dependencies

8. Uninstalling a package
```
sudo aptitude purge package-name
aptitude remove package-name

```
The first one deletes everything including configuration files. The second one retains the configuration files. 

9. Listing all files that a certain package installed in your system
```
dpkg --listfiles package-name
```

10. Finding out which package installed a file
If you know a file, and want to know which package installed it
```
dpkg --search filename
```
For example dpkg --search /etc/apache2/apache2.conf reveals apache2-common

11. Upgrading your system
```
sudo aptitude upgrade
```
This upgrades all packages installed using aptitude/apt-get or dpkg. Substitute upgrade with dist-upgrade for a more complete upgrade (can someone help me out here?)

12. Finding out which repo a package came from
```
apt-cache policy package_name
```

13. Changing configuration of a package
```
sudo dpkg-reconfigure package-name
```

14. Clear the cache of downloaded packages
```
sudo aptitude clean
sudo aptitude autoclean

```

15. Show informatoin about a package
```
aptitude show package-name
apt-cache show package-name
dpkg --info package-name.deb 

```
The last one is for showing details of a package you downloaded online. 

Other miscellaneous details

1. apt-get settings in /etc/apt. Change if you know what you are doing 
You could
--- Determine before hand how much configuration a package should undergo
--- modify the gpg data of repositories
--- Pin packages, that determine wheter or not you don't want a package upgraded

2. Downloaded .deb files are stored in /var/cache/apt/archives
Delete them using 14


If required, admins please move this to another section as you see fit.

Edit #1: Thanks to Aysiu for pointing out requirement of root permisions.

---

### Post by Ziox on 2006-08-01
this is awesome!!! I'm so glad that you used "aptitude" instead of "apt-get"

---

### Post by aysiu on 2006-08-01
I realize you use Debian, too, but most of the readers on this forum are Ubuntu users--you might want to plop a *sudo* in there for some of those commands. Otherwise, a handy reference.

---

### Post by SentientFluid on 2007-03-28
Excellent reference material, though it didn't have the one thing I was looking for...

If I do not want to download an update, how can I mark it so it stops showing up when I want to update.  I know I can *sudo aptitude hold packagename* to keep it from installing, but it still always detects it and tells me I have updates waiting?

If it makes a difference, I'm running Dapper.

---

