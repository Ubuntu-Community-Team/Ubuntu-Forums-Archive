---
title: "Envy won't install"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-19
After I download envy the package installer pops up and gives me this error and won't let me install

Error: Dependency is not satisfiable: build-essential

---

### Post by Dapman01 on 2007-10-19
bump

---

### Post by Wiebelhaus on 2007-10-19
Install the dependency with:

```
sudo apt-get install build-essential
```

Definition: build-essential: Informational list of build-essential packages If you do not plan to build Debian packages, you don't need this package. Moreover this package is not required for building Debian packages. This package contains an informational list of packages which are considered essential for building Debian packages. This package also depends on the packages on that list, to make it easy to have the build-essential packages installed. If you have this package installed, you only need to install whatever a package specifies as its build-time dependencies to build the package. Conversely, if you are determining what your package needs to build-depend on, you can always leave out the packages this package depends on. This package is NOT the definition of what packages are build-essential; the real definition is in the Debian Policy Manual. This package contains merely an informational list, which is all most people need. However, if this package and the manual disagree, the manual is correct. 

................................. 
Source: Debian 3.0r0 APT / Linux Dictionary V 0.16 
[http://www.tldp.org/LDP/Linux-Dictionary/html/index.html](http://www.tldp.org/LDP/Linux-Dictionary/html/index.html) 
Author: Binh Nguyen linuxfilesystem(at)yahoo(dot)com(dot)au 
.................................

---

### Post by Dapman01 on 2007-10-19
> **sx66gns said:**
> Install the dependency with:

```
sudo apt-get install build-essential
```

Definition: build-essential: Informational list of build-essential packages If you do not plan to build Debian packages, you don't need this package. Moreover this package is not required for building Debian packages. This package contains an informational list of packages which are considered essential for building Debian packages. This package also depends on the packages on that list, to make it easy to have the build-essential packages installed. If you have this package installed, you only need to install whatever a package specifies as its build-time dependencies to build the package. Conversely, if you are determining what your package needs to build-depend on, you can always leave out the packages this package depends on. This package is NOT the definition of what packages are build-essential; the real definition is in the Debian Policy Manual. This package contains merely an informational list, which is all most people need. However, if this package and the manual disagree, the manual is correct. 

................................. 
Source: Debian 3.0r0 APT / Linux Dictionary V 0.16 
[http://www.tldp.org/LDP/Linux-Dictionary/html/index.html](http://www.tldp.org/LDP/Linux-Dictionary/html/index.html) 
Author: Binh Nguyen linuxfilesystem(at)yahoo(dot)com(dot)au 
.................................
So what do I need to do to get envy?

---

### Post by por100pre1 on 2007-10-19
```
gksudo software-properties-gtk
```

Check that main, universe, multiverse and restricted are enabled.

Put the envy package in your desktop.

```
cd Desktop
```

```
sudo gdebi -i envy_0.9.8-0ubuntu8_all.deb
```

post any errors you see... :-k

---

### Post by overlord.gaurav on 2007-10-19
I remember Envy having a set of dependencies.
If you still get some dependency problem after you have done sxgns's command, then try this:    *you can try it before his command as well*

```
sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
```

EDIT: Ok, I read your next post kind of late. Maybe [this link]("http://albertomilone.com/latest_nvidia_udsf_feisty.html#REQUIREMENTS") sorts your problem.

---

### Post by Pumalite on 2007-10-19
Do what you were doing before now that you have build-essential installed.

---

### Post by Dapman01 on 2007-10-19
> **overlord.gaurav said:**
> I remember Envy having a set of dependencies.
If you still get some dependency problem after you have done sxgns's command, then try this:    *you can try it before his command as well*

```
sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
```

EDIT: Ok, I read your next post kind of late. Maybe [this link]("http://albertomilone.com/latest_nvidia_udsf_feisty.html#REQUIREMENTS") sorts your problem.

This is what I got after that first part
gdebi: error: no such option: -i
patrick@patrick-desktop:~/Desktop$ sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
patrick@patrick-desktop:~/Desktop$

---

### Post by MenZa on 2007-10-19
Sigh. Don't install Envy; you'll end up breaking your system when you decide to update, or something similar. Instead, try telling us which video card you have, so we can point you in the direction of installing your driver correctly.

---

### Post by Pumalite on 2007-10-19
You'll need headers and buid-essential installed to compile your driver into the kernel anyway.

---

### Post by cvcuse on 2007-10-24
Had nvidia driver for geforce 8400gs working great on vostro 1400  before upgrade to gutsy. No go now. Used 'envy' method. Have decided to  try and install nvidia driver on another feisty partition that hasn't been upgraded. All help appreciated.

---

