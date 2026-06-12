---
title: "source forge packages"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Paul Barnett on 2008-01-21
I want to install a package, postbooks, from source forge. What is the best way to do that?

---

### Post by Cypher on 2008-01-21
You would be compiling from source..so grab the .TAR.GZ from Sourceforge..then run the following command to ensure you have the basic build environment
```

sudo apt-get install build-essential

```
Now, uncompress the .TAR.GZ for Postbooks and read the README/INSTALL whatever they have in there. It looks like, at the least, you're going to need the QT libraries installed. But there might be others..once you have all the libraries installed you should be able to do the following
```

sudo apt-get install checkinstall
cd <postbooks directory>
./configure
make
checkinstall

```
The checkinstall package will create a .DEB file from the sources you've compiled, you can then do
```

sudo dpkg -i <newly created postbooks>deb

```
to install the DEB..

---

