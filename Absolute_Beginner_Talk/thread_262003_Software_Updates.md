---
title: "Software Updates"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2006-09-21
I appear to have a an update stuck in the Automatic Software Update area. A pop-up appears indicating an error "The following problem were found on your system: /var/cache/apt/archives/openoffice.org-core2.0.2-2ubuntu12.1_i386.deb :supprocess dpkg-deb --fsys-tarfile returned error exit status 2

I do not know what to do or how to rectify this error, I thought I could manually download the file again but how do I do that or delete the file but I do not have the permission to do that, even though I am the only one that uses this machine.  Help please and thanks in advance,
Old Kevin

---

### Post by mssever on 2006-09-21
I would open up a terminal (Applications > Accessories > Terminal) and type:
```
sudo apt-get remove openoffice.org-core
```
Note any other packages you have to remove.

Now, do:
```
sudo apt-get install openoffice.org-core/dapper
``` Add any packages automatically removed in the previous step to the end of the command, separated by spaces.

---

### Post by Kevin Funnell on 2006-09-23
G'Day,

I received an error when I trying Code: [COLOR="Blue"]sudo apt-get install openoffice.org-core/dapper[/COLOR] Keeps coming up with the original error (from my first post).

As I can not install this package as it keeps being reported as as [COLOR="Red"]Broken[/COLOR] and I seem to be going around in circles.

How can I remove it from my system(computer) ([COLOR="Blue"]E:/var/cache/apt/archives/openoffice.org-core[/COLOR]) I do not have premission/previlage to do it (owner: root) and re-install the OpenOffice.org program/package, via either a fresh  download or from the original Ubuntu CD.  

Any help would be greatly appreciated & Thanks in advance,

Old Kevin

---

### Post by chrisfay on 2006-09-23
You might try purging the package then deleting the cache'd file before reinstalling:

```
sudo apt-get --purge remove openoffice.org-core
```

```
sudo rm /var/cache/apt/archives/openoffice.org-core
```

```
sudo aptitude install openoffice.org-core
```

---

