---
title: "apt-get install problem"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-11
when i am going to install ytalk ?
 
-------------------------------------------------------------------------------
tom@ubuntu7.04:~$ sudo apt-get install ytalk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ytalk
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
Need to get 43.7kB of archives.
After unpacking 147kB of additional disk space will be used.
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe ytalk 3.3.0-2
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/y/ytalk/ytalk_3.3.0-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/y/ytalk/ytalk_3.3.0-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
tom@ubuntu7.04:~$ 
---------------------------------------------------------
how to solve this ?



thanks

---

### Post by avik on 2007-10-11
Try running:

```
sudo apt-get update
```

Also, while this isn't necessarily related to your problem, run:

```
sudo apt-get upgrade
```

You seem to have a lot of outdated packages.

---

### Post by mokkai on 2007-10-11
when i try this ....

tom@ubuntu7.04:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_IN       
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_IN     
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg        
....
....
....
verse/binary-i386/Packages.gz  Could not resolve 'in.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tom@ubuntu7.04:~$


how to sole this ?

---

### Post by mokkai on 2007-10-11
tom@ubuntu7.04:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gaim
The following packages will be upgraded:
  app-install-data-commercial libkadm55 libkrb5-dev libkrb53 libmagick9
  libpq-dev libpq5 libsndfile1 libssl-dev libssl0.9.8 linux-headers-2.6.20-16
  linux-headers-2.6.20-16-generic linux-image-2.6.20-16-generic linux-libc-dev
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-style-human openoffice.org-writer openssl postgresql-8.2
  postgresql-client-8.2 python-uno tk8.4 tk8.4-dev ttf-opensymbol
...
...
...
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4-dev_8.4.14-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4-dev_8.4.14-0ubuntu2.1_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.14-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.14-0ubuntu2.1_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.25_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.25_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vnc4/vnc4server_4.1.1+xorg1.0.2-0ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vnc4/vnc4server_4.1.1+xorg1.0.2-0ubuntu4.1_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
tom@ubuntu7.04:~$

---

### Post by russell.h on 2007-10-11
Is your internet working on that computer?

---

### Post by mokkai on 2007-10-11
yes, if not then  ,how i message to you ?

---

### Post by Beggar on 2007-10-12
The reason he asked is because the problem your having is your computer can't connect to the archive server. It seems like you have it configured to get from the in (india?) repos, can you ping those machines?

```
ping in.archive.ubuntu.com
```

---

