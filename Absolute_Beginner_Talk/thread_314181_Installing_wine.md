---
title: "Installing wine"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Psystorm on 2006-12-07
For some reason I'm getting this error.

sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

Thanks in advance.

-Alex

---

### Post by foxmulder881 on 2006-12-07
Are you trying to install it on 32bit or 64bit?

---

### Post by Psystorm on 2006-12-07
> **foxmulder881 said:**
> Are you trying to install it on 32bit or 64bit?

32 bit I think.  I used the default installation cd.

---

### Post by Psystorm on 2006-12-07
Update:
apt-cache search wine returns nothing even after I ran apt-get update.  (Using dapper)  Any help would be appreciated thanks a lot.

---

### Post by ajgreeny on 2006-12-07
Make sure your universe and multiverse repos are active and you'll find it there using apt-get.

---

### Post by Afoot on 2006-12-09
You haven't got wine's repositories added.

First, you have to add the repositories, so edit the file.
```
sudo gedit /etc/apt/sources.list
```

Then, you need to add the following lines to the end (or anywhere else in it):
```
# Repository for wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

Then just save the file, and do:
```
sudo apt-get update
sudo apt-get install wine
```

And then you should have Wine. ;)

---

### Post by sub7 on 2006-12-09
```
clickme@clickme-desktop:~$ sudo gedit /etc/apt/sources.list
clickme@clickme-desktop:~$ sudo apt-get update
Ign http://wine.budgetdedicated.com edgy Release.gpg
Ign http://wine.budgetdedicated.com edgy/main Translation-en_GB
Hit http://wine.budgetdedicated.com edgy Release
Ign http://wine.budgetdedicated.com edgy/main Packages
Ign http://wine.budgetdedicated.com edgy/main Sources
Errhttp://wine.budgetdedicated.com edgy/main Packages
  404 Not Found
Get: 1 http://wine.budgetdedicated.com edgy/main Sources [638B]
Fetched 638B in 0s (1494B/s)
Failed to fetch http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
clickme@clickme-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
```

---

### Post by LDRoamer on 2006-12-09
I used automatix to install wine. That worked fine for me. You might try that.

---

### Post by konst88 on 2006-12-09
This is the correct line for the sources.list:
```
deb http://wine.budgetdedicated.com/apt edgy main
```

---

### Post by Afoot on 2006-12-10
> **sub7 said:**
> ```

Failed to fetch http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz  404 Not Found

```
OK, you are trying to get a package for 64-bit ubuntu. It won't work now though, and if wine were to be compiled on a 64-bit platform, it wouldn't work too well with your standard 32-bit windows programs, would it? So what you should do, is to download the *Wine 0.9.26* deb from [Wine's archive]("http://wine.budgetdedicated.com/archive/index.html"). Version 0.9.27 is the newest, but they haven't made a deb for it, yet.

When download is finished, *cd* to the directory of the deb and use this command to install the package:
```
sudo dpkg -i --force-architecture replace_with_pkg_name
```

You have to put the *--force-architecture* there, as you are trying to install a package of non-native architecture (32-bit).

If the package won't install, or if you can't run anything with it, you are probably missing 32-bit 'emulation' packages. You can find some of them here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=ia32&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=ia32&sourceid=mozilla-search)

---

