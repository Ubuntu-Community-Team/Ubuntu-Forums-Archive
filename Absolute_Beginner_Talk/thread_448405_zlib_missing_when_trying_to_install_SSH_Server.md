---
title: "zlib missing when trying to install SSH Server"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Darkriser on 2007-05-19
Sorry for duplicate thread ([http://ubuntuforums.org/showthread.php?t=411492]("http://ubuntuforums.org/showthread.php?t=411492")), but I need to install SSH Server and I'm getting following error:

configure: error: *** zlib missing - please install first or check config.log ***

Anyone knows what package should I install?
I have a fresh and default installation of Feisty.

Thanx a lot.
Marcel

---

### Post by heimo on 2007-05-19
Try installing zlib1g-dev
```
sudo apt-get install zlib1g-dev
```

If you're compiling openssh-server, you could probably use this to get all build dependencies:
```
sudo apt-get build-dep openssh-server
```

---

### Post by Darkriser on 2007-05-19
worked, thanx a lot, again!

---

### Post by cmoibal on 2007-09-28
bonjour je pense ke l'architecture de compilation est la raison de votre erreur... si tous les biblio sont presents, alors verifier que le binaire de zlib est bien celui de votre architecture ....

cmoibal:$ file /usr/lib/libz.so.x.x.x.x

---

### Post by leo83 on 2008-05-29
> **heimo said:**
> Try installing zlib1g-dev
```
sudo apt-get install zlib1g-dev
```

If you're compiling openssh-server, you could probably use this to get all build dependencies:
```
sudo apt-get build-dep openssh-server
```


While executing  2nd command , i get following error, how do i overcome it?
```

pc2:/srv/krone/Mini-Controller/Codebase_2.5.0.0/PoE# sudo apt-get build-dep openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/ftp.de.debian.org_debian_lenny_dists_main_contrib_source_Sources - open (2 No such file or directory)



```

Thanks

---

