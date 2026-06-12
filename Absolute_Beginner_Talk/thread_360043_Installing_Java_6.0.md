---
title: "Installing Java 6.0"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-12
I would like to install the Sun java sdk 6.0. According to other forums that I have seen I need to use the make-jpkg utility however, when i attempted to install it using
sudo apt-get install make-jpkg, it said that it could not find it? Does anyone how I could get it? I am using version 6.06 version rite now. And when I install the new package, how do i configure linux to make that the default java.

---

### Post by jvc26 on 2007-02-12
I compiled java 1.6.0 using the instructions here:
> **mlind said:**
> Well it doesn't seem to. I'll attach a debdiff to get sun-java6 support for java-package.


To get current java-package, you must add multiverse source repository in /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

```

Then patch and build java-package
```

mkdir /tmp/java-package
cd /tmp/java-package
apt-get source java-package
cd java-package-0.28
patch -p1 < /path/to/**java-package_sun-java6.patch**

sudo aptitude install debhelper
debian/rules binary
sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

```

Build java6 binaries
```

sudo aptitude install fakeroot
fakeroot make-jpkg **jdk-6-linux-i586.bin**

```

/edit
I forgot to attach already patched .deb
/edit2
patch was missing j2re install and remove scripts

Il

---

### Post by phossal on 2007-02-12
JDK 6 is ready-made in two places. If you enable the backports, you can download the third-party package: *sun-java6-jdk*. If you're not a total novice, you'll want to download your Java directly from SUN. Instructions for installing it are included in my signature.

---

