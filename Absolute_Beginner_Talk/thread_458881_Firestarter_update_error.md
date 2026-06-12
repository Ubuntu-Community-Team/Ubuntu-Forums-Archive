---
title: "Firestarter update error"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-05-30
Hi, I am having the following error message when updating via update manager:

```
A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.
```

And when carrying out install via apt-get:

```
user@user-pc:~$ apt-get install firestarter
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
user@user-pc:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
firestarter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up firestarter (1.0.3-1.1ubuntu4.1) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help please :(

---

### Post by pebo on 2007-05-30
```
sudo apt-get install firestarter
```;)

---

### Post by geezerone on 2007-05-30
:D You mean like I did the second time ;)

```
user@user-pc:~$ apt-get install firestarter
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
user@user-pc:~$ **sudo apt-get install firestarter**
```

Anyone??

---

### Post by pebo on 2007-05-31
First make sure apt / synaptic / aptitude / update-manager are shut down. Then try: ```
sudo dpkg --configure -a
``` and try again.
If it still won't play try renaming the lock file:```
sudo mv /var/lib/dpkg/lock/var/lib/dpkg/lock.old 
```HTH

---

### Post by Bigdog60 on 2007-05-31
Dude you got to shut down the symantec update manager. delte the previously installed and then reinstall.

---

### Post by geezerone on 2007-06-13
No joy after dpkg or uninstall/reinstall and get the following error:

```
E: firestarter: subprocess post-installation script returned error exit status 2

```

Any ideas?

EDIT: This happened after upgrade via repositories a few weeks ago.

---

### Post by mail480697 on 2007-06-14
FWIW my firestarter is also broken:

$ sudo apt-get  install firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firestarter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up firestarter (1.0.3-1.2ubuntu3.2) ...
 * Starting the Firestarter firewall...
   ...fail!
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ sudo /etc/init.d/firestarter start
 * Starting the Firestarter firewall...
   ...fail!

I'm trying to find out what happened to cause :

dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2

but I'm not sure where to look.

FWIW the problem seemed to start with the upgrade to  1.0.3-1.2ubuntu3.2

---

### Post by geezerone on 2007-06-14
**mail480697** - 

```
sudo apt-get remove --purge firestarter
```

then,

```
sudo apt-get install firestarter
```

This worked easily for me and hope it does for you also.

Regardez

---

