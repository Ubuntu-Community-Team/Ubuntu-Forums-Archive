---
title: "Problem installing FreeNX on G4 Hardy"
date: 2008-12-19
forum: Apple Hardware Users
---

### Post by SalemMA on 2008-12-19
I successfully installed Ubuntu 8.04 Hardy on my wife's old Quicksilver G4 PowerPC.

Now I want to install FreeNX on it.

When I tried the following:[INDENT][SIZE=1]user@G4-Ubuntu:~/freenxsource$ apt-get -b source nx freenx
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Skipping already downloaded file 'nx_3.3.0-3-6.orig.tar.gz'
Skipping already downloaded file 'nx_3.3.0-3-6-0freenxteam9.diff.gz'
Skipping already downloaded file 'nx_3.3.0-3-6-0freenxteam9.dsc'
Skipping already downloaded file 'freenx-server_0.7.3+svn612.orig.tar.gz'
Skipping already downloaded file 'freenx-server_0.7.3+svn612-0freenxteam10.diff.gz'
Skipping already downloaded file 'freenx-server_0.7.3+svn612-0freenxteam10.dsc'
Need to get 0B of source archives.
sh: dpkg-source: not found
Unpack command 'dpkg-source -x nx_3.3.0-3-6-0freenxteam9.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed
user@G4-Ubuntu:~/freenxsource$[/SIZE][/INDENT]It appears that the correct source files for FreeNX have been downloaded but that I lack the dpkg-dev package needed (I gather) to install *.dsc packages (that's a debian package?).

In any case, if someone can give some help installing the missing dpkg-dev package on a G4/PowerPC running Ubuntu 8.04, it would be appreciated.

TIA, Doug

---

### Post by SalemMA on 2008-12-21
OK, I have resolved most of the lingering dependencies...

But I have one (I hope it's the last one   :confused: ) which is the following:

libxcompext-dev

Does anyone know how I can get this installed on a Hardy PowerPC system?

TIA, Doug

---

### Post by cyberdork33 on 2008-12-22
Easy way to get build dependencies:
```
sudo apt-get build-dep *packagename*
```

---

### Post by SalemMA on 2008-12-24
> **cyberdork33 said:**
> Easy way to get build dependencies:
```
sudo apt-get build-dep *packagename*
```

Thanks... I seem to have narrowed it down to one remaining package (although I suppose it may have its own dependencies).

But when I execute the code you suggest I get the following:
[INDENT]user@G4-Ubuntu:~/foo$ sudo apt-get build-dep libxcompext-dev
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
user@G4-Ubuntu:~/foo$


[/INDENT]Any suggestions as to a next step?

TIA, SalemMA

---

### Post by tomkerswill on 2009-01-07
Hi

I'm trying to do the same thing and found your forum post. That missing dependency, libxcompext-dev, is contained within a third package, which is also in the FreeNX repository. So before doing building freenx and nx, I found that you need to do:

sudo apt-get build-dep nxcomp
sudo apt-get -b source nxcomp

That should then build then necessary packages, and you can continue with the other steps..

Tom

---

