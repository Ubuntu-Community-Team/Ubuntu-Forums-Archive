---
title: "Debian Deskbar"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by RoseHeyworth on 2007-03-09
1. How do i get/download the debian deskbar? i am using Ubuntu 6.10 Edgy Eft

2. Installing through the terminal of any programs go something like this:

sudo apt-get install sdl_image-1.2.5.tar.gz
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sdl_image-1.2.5.tar.gz

3. Try to install anything from respositories brings this:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


I understand tarballs need another sort of platform to open but guess what,that is the platform and i cant even install that?!!?!?!?

any help would be great!

thanks

Kristian

---

### Post by joselin on 2007-03-09
```
sudo apt-get install deskbar
```

---

### Post by 23meg on 2007-03-09
> 1. How do i get/download the debian deskbar? i am using Ubuntu 6.10 Edgy Eft

Deskbar isn't specific to Debian, and it comes preinstalled with Edgy; do you mean that you'd like to install the version of Deskbar that's in Debian? If you just want to use it, right click your panel, choose "Add To Panel" and choose "Deskbar".

> 2. Installing through the terminal of any programs go something like this:

sudo apt-get install sdl_image-1.2.5.tar.gz
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sdl_image-1.2.5.tar.gz


You don't install source tarballs through apt-get; you compile them. For the basics of installing applications, check these out:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)


> 3. Try to install anything from respositories brings this:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


I understand tarballs need another sort of platform to open but guess what,that is the platform and i cant even install that?!!?!?!?

If your internet connection is working, you probably have an erroneous line in your /etc/apt/sources.list file. Posting its contents would help.

---

### Post by RoseHeyworth on 2007-03-09
Hi, heres what happens when i do that:

sudo apt-get install deskbar
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deskbar

Where is E: located?

---

### Post by RoseHeyworth on 2007-03-09
Regarding my third question, here is the outcome:

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

Am i being stupid in reading that the service would be denied due to my proxy authentication?

---

### Post by 23meg on 2007-03-09
> Hi, heres what happens when i do that:

You don't need to install Deskbar in Edgy; it's already installed by default. Just add it to your panel as I described.

---

