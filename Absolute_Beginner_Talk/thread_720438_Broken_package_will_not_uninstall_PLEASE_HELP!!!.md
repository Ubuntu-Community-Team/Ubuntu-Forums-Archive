---
title: "Broken package will not uninstall PLEASE HELP!!!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by k420 on 2008-03-10
I installed a package from the brother website called mfc9700lpr when i try to remove it i get error code 127```
udo dpkg --remove --force-remove-reinstreq mfc9700lpr
(Reading database ... 297597 files and directories currently installed.)
Removing mfc9700lpr ...
/var/lib/dpkg/info/mfc9700lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc9700lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc9700lpr

```
I cant install a plugin for pidgin because of this it says i am missing dependencies.  any one know how to remove this PLEASe
I get this if i try this ```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kaffeine libxine1-gnome
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mfc9700lpr
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 297597 files and directories currently installed.)
Removing mfc9700lpr ...
/var/lib/dpkg/info/mfc9700lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc9700lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc9700lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
nathan@nathan-laptop:~$                       
```

---

### Post by bodhi.zazen on 2008-03-10
You may be able to remove it by creating an empty file :

```
sudo touch /etc/init.d/lpd
```

The re-try removal.

If all else fails you may need to manually remove it. 

```
sudo locate mfc9700lpr
```

Delete those files ...

---

### Post by k420 on 2008-03-10
Here is what i get when i do that and let me know if i did it right ```
nathan@nathan-laptop:~$ sudo touch /etc/init.d/lpd
nathan@nathan-laptop:~$ sudo locate mfc9700lpr
/var/lib/dpkg/info/mfc9700lpr.conffiles
/var/lib/dpkg/info/mfc9700lpr.list
/var/lib/dpkg/info/mfc9700lpr.postrm
/var/lib/dpkg/info/mfc9700lpr.postinst
/var/lib/dpkg/info/mfc9700lpr.prerm
/var/crash/mfc9700lpr.0.crash
nathan@nathan-laptop:~$   
```

---

### Post by bodhi.zazen on 2008-03-10
Looks good. Try to remove the package again and post any errors.

sudo dpkg --remove --force-remove-reinstreq mfc9700lpr

---

### Post by k420 on 2008-03-10
```
sudo dpkg --remove --force-remove-reinstreq mfc9700lpr
(Reading database ... 297426 files and directories currently installed.)
Removing mfc9700lpr ...
/var/lib/dpkg/info/mfc9700lpr.postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error processing mfc9700lpr (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 mfc9700lpr

```

---

### Post by bodhi.zazen on 2008-03-10
First. lets confirm that that file is empty :

```
sudo cat /etc/init.d/lpd
```

If it is NOT empty, copy it to a backup

sudo cp /etc/init.d/lpd /etc/init.d/lpd.back

Then, lets give it permission :

```
sudo chmod 777 /etc/init.d/lpd
```

And re-run 

sudo dpkg --remove --force-remove-reinstreq mfc9700lpr

---

### Post by k420 on 2008-03-10
hey that worked thanks so much

---

