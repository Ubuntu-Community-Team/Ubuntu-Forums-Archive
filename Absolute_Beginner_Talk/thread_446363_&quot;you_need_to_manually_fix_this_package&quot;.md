---
title: "&quot;you need to manually fix this package&quot;"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by niltub on 2007-05-16
Hi all,

I cleaned up some obsolete files the other day through Synaptic Package Manager, but have run into troubles when one of the files, an old linux-header file, was not removed (current linux header, 2.6.20-15, linux header that can't be removed, 2.6.17-11).  In fact, it is quite stubborn and I can't get rid of it now at all. It is permanently marked for removal, I can't unmark it for removal, and I can't install / uninstall any other packages because this error come up no matter what I do:

E: I wasn't able to locate file for the linux-headers-2.6.17-11 package. This might mean you need to manually fix this package.

I have tried the solutions posted to a similar problem in [another forum message]("http://ubuntuforums.org/showthread.php?t=439725") , with the following result:

```

#####-laptop:~$ sudo dpkg --configure -a

#####-laptop:~$ sudo aptitude clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

#####-laptop:~$ sudo aptitude update
Get:1 http://au.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://au.archive.ubuntu.com feisty/main Translation-en_AU
Ign http://au.archive.ubuntu.com feisty/universe Translation-en_AU
Ign http://au.archive.ubuntu.com feisty/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com feisty/multiverse Translation-en_AU
Get:2 http://au.archive.ubuntu.com feisty Release [57.2kB]
Hit http://au.archive.ubuntu.com feisty/main Packages
Hit http://au.archive.ubuntu.com feisty/universe Packages
Hit http://au.archive.ubuntu.com feisty/restricted Packages
Hit http://au.archive.ubuntu.com feisty/multiverse Packages
Hit http://au.archive.ubuntu.com feisty/main Sources
Hit http://au.archive.ubuntu.com feisty/universe Sources
Hit http://au.archive.ubuntu.com feisty/restricted Sources
Hit http://au.archive.ubuntu.com feisty/multiverse Sources
Fetched 57.2kB in 0s (153kB/s)
Reading package lists... Done

#####-laptop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the linux-headers-2.6.17-11 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

```

And have tried another "solution" I found searching the web:

```

#####-laptop:~$ sudo dpkg --remove linux-headers-2.6.17-11
(Reading database ... 141473 files and directories currently installed.)
Removing linux-headers-2.6.17-11 ...
dpkg: error processing linux-headers-2.6.17-11 (--remove):
 cannot remove file `/usr/src/linux-headers-2.6.17-11/include/config/MARKER': Not a directory
Errors were encountered while processing:
 linux-headers-2.6.17-11

```

Does anyone have any suggestion?  Your help would be GREATLY appreciated!

Mark.

---

### Post by mitch.c on 2007-05-16
What happens if you:
```
$ sudo aptitude -f install
```
-- 
Mitch

---

### Post by niltub on 2007-05-17
Thanks for your reply Mitch.  Doing 'sudo aptitude -f install' resulted in a huge list of packages to be installed, and removed, but would not go ahead because of the same error again:

```

...
0 packages upgraded, 19 newly installed, 73 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 243MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: I wasn't able to locate file for the linux-headers-2.6.17-11 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

```

So, still looking for this alleged 'manual fix'...

---

### Post by mitch.c on 2007-05-17
If it's a problem with the package cache, may be this will help:
```
$ sudo aptitude clean
```

---

### Post by Bachstelze on 2007-05-17
REinstall it from the DEB (with dpkg -i).

---

### Post by niltub on 2007-05-17
Thanks Mitch and HymnToLife,

The 'sudo aptitude clean' did not fix it, but installing the package again from a deb package of linux-header-2.6.17-11 cleared it all up (had to download from internet, as it is no longer in the repositories according what was coming up at the terminal).

Thanks very much for your help!!

---

