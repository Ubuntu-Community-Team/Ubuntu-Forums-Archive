---
title: "Problems upgrading to 7.10"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2008-02-26
hi
i have 7.04 64bit, everytime i try to upgrade to 7.10 i get this

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)

please can some1 help, and let me know if upgrading will cause any problems with the data i have on my hard drive...?

---

### Post by forestpixie on 2008-02-26
open your sources to edit and comment those lines out with a # at the front of each

gksudo gedit /etc/apt/sources.list

if they're not all in there - look for the medibuntu sources list which can be seperate

---

### Post by ajgreeny on 2008-02-26
As you may have noticed by now these are all feisty repos, and you're trying to upgrade to gutsy, so they are no use and worse, are causing problems to the upgrade.  The file you need is probably in **/etc/apt/sources.list.d** folder as [B]medibuntu.list.

[/B]I have never done an upgrade, only a clean install, as I tend to change my system too much for an upgrade to work very well, but I wonder what would happen if you change all the occurrences of **feisty** to **gutsy** in those repos' urls.  Could be worth trying.

---

### Post by forestpixie on 2008-02-26
personally as it always seems to take forever and a day to get the mirrors scanned I tend to disconnect the router and then deal with the fallout after the install has finished - even on a clean install

---

### Post by NeoEIRE on 2008-02-26
reply to Forestpixie....

i am not sure if i done it write? i added ur command to the terminal and got this...

neoeire@neoeire-desktop:~$ gksudo gedit etc/apt/sources.list
(gedit:19610): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
neoeire@neoeire-desktop:~$ 


am i better off just doing a clean reboot to 7.10? plus does any1 know if games like battlefield2
and simcity4 rush hour work on 7.10 as i have never managed to get any of my games to work before...?

thanks for the help

---

### Post by forestpixie on 2008-02-27
d'oh - my fault typo 

```
gksudo gedit /etc/apt/sources.list
```

might need to do the same to 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

check out the wine application database for the games - [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

