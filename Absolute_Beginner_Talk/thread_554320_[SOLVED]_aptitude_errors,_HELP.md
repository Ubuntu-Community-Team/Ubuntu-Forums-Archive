---
title: "[SOLVED] aptitude errors, HELP"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-09-18
I don't know what happened but this error keeps popping up and refraining me from installing or removing any program. Please help, I don't know where to begin. Thanks

```

$ sudo aptitude vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up spe (0.8.2a+repack-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
dpkg: error processing spe (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
 spe
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up spe (0.8.2a+repack-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
dpkg: error processing spe (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 spe

```

---

### Post by alienexplorers on 2007-09-18
Have you tried running
> sudo aptitude update
and
> sudo aptitude upgrade
before trying to load the software package.

---

### Post by mikawber on 2007-09-18
yes I have about 10 times

---

### Post by alienexplorers on 2007-09-18
Do you already have vmware-player installed?  It seems like your machine thinks you do for some strange reason.

---

### Post by Dr Small on 2007-09-18
> **mikawber said:**
> yes I have about 10 times
I never try anything more than 3 times, because the forth is the same as the third. :D

---

### Post by brennydoogles on 2007-09-18
> **mikawber said:**
> I don't know what happened but this error keeps popping up and refraining me from installing or removing any program. Please help, I don't know where to begin. Thanks

```

**_$ sudo aptitude vmware-player_**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up spe (0.8.2a+repack-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
dpkg: error processing spe (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
 spe
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up spe (0.8.2a+repack-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
dpkg: error processing spe (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 spe

```

Shouldn't that be ```
sudo aptitude **_install_** vmware-player
```??

---

### Post by mikawber on 2007-09-18
yea I copied it wrong sorry

---

### Post by mikawber on 2007-09-18
when I try to uninstall vmware-player it says this 

```

$ sudo aptitude remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.20-16 
The following packages will be REMOVED:
  vmware-player 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 35.9MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 144552 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing vmware-player-kernel-modules ...
Removing vmware-player-kernel-modules-2.6.20-16 ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by mikawber on 2007-09-18
Hey, thanks for the replies but I was able to fix it by installing it from source and then uninstalling it.

---

