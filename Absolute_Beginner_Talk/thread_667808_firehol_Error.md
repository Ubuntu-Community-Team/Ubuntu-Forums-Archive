---
title: "firehol Error"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Jim Shunamon on 2008-01-14
Hello all,
Every time I try and install a package either from the command-line or with Synaptic I get an error message that reads:
"An Error Occured. E: firehol: Subprocess post-installation script returned error exit status 1."
Sometimes the packages have installed despite this error and sometimes they have not. Does anyone know how I can fix this?
Thank you all and God bless.
><>  Jim Shunamon  <><

---

### Post by SOULRiDER on 2008-01-14
Try these commands
```
sudo aptitude update
sudo aptitude dist-upgrade
```

They will most likely give you an error, paste the output.

---

### Post by SOULRiDER on 2008-01-14
Actually, i think this is the command you need to run
```
sudo dpkg --configure -a
``` (mind the double - before configure)

---

### Post by Jim Shunamon on 2008-01-14
Thanks SoulRider.
I am using Ubuntu CE 3.3 (Feisty) and don't really want to have to do a distro upgrade until the official  Ubuntu CE is upgraded as I depend on all of the pre-installed Bible software on a daily basis. I am afraid if I do a distribution upgrade I will get the regular version of Ubuntu without all of the Bible software and this is not what I need at this point.
Is there any way that I can do the upgrade and still keep all of the Bible stuff without having to download it all? Also, I could never deal with trying to configure it all under Wine.
Thanks.
><>  Jim  <><

---

