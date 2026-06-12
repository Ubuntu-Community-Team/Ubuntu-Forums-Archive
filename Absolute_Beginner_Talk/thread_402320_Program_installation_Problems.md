---
title: "Program installation Problems"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Hymn on 2007-04-05
Ok... at first I thought it was just a problem with installing beryl, but now I've encountered this same problem in installing any program through the terminal (and symantic).  For some reason it doesn't install the files... well here...

I tried to install IEs4Linux, because I have math homework which requires me to use an IE based browser to view it (stupid, because it works in firefox w/ activx just fine) and I get this error when installing Wine


> hymn@hymn-laptop:~$ sudo apt-get install wine cabextract
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
wine: 
Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed   
Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed    
Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed      
Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed 
Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages



The same exact error happened with Beryl.  What is wrong?

---

### Post by dbbolton on 2007-04-05
run ```
sudo aptitude install -f
``` to fix broken packages.

---

### Post by Hymn on 2007-04-05
> **dbbolton said:**
> run ```
sudo aptitude install -f
``` to fix broken packages.

> 
hymn@hymn-laptop:~$ sudo aptitude install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been kept back:
  bluez-pcmcia-support foomatic-db-gutenprint gok gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  ijsgutenprint libcompfaceg1 libgnutls12 libnetcdf3 libtasn1-2 libwnck18
  pcmcia-cs python-gadfly python-htmltmpl python-kjbuckets python-netcdf
  python-parted python-pgsql python-soappy python-stats python-syck
  x-window-system-core
0 packages upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


Didn't do anything, be more specific?

---

### Post by dbbolton on 2007-04-05
it did something. did you try whatever beryl stuff you have to do after that ?

---

### Post by Hymn on 2007-04-05
> hymn@hymn-laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  bluez-pcmcia-support foomatic-db-gutenprint gok gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  ijsgutenprint libcompfaceg1 libgnutls12 libnetcdf3 libtasn1-2 libwnck18
  pcmcia-cs python-gadfly python-htmltmpl python-kjbuckets python-netcdf
  python-parted python-pgsql python-soappy python-stats python-syck
  x-window-system-core
0 packages upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


hymn@hymn-laptop:~$ sudo apt-get install wine cabextract
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be insta lled
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages


I space it out a bit so you could see what I put in.  This is trying to install wine.

---

### Post by dbbolton on 2007-04-05
```
sudo aptitude dist-upgrade
```

will force all upgrades (those packages being held back). but this can be dangerous.

---

### Post by Hymn on 2007-04-05
> **dbbolton said:**
> ```
sudo aptitude dist-upgrade
```

will force all upgrades (those packages being held back). but this can be dangerous.

I ran it once, no good... theres multiple options though


Just wondering, but is there a reason the system is holding back those packages in the first place?

---

### Post by Hymn on 2007-04-05
still having problems >_> help me?

---

