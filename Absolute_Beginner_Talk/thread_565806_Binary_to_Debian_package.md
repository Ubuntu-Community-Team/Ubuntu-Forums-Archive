---
title: "Binary to Debian package"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by CSMatt on 2007-10-02
I've seen several threads that explain how to turn a source code tarball unto a Debian package, but what if you are given a distribution-neutral **binary** tarball?  How do I turn that into a Debain package?

---

### Post by Pumalite on 2007-10-02
[http://linux.die.net/man/1/alien](http://linux.die.net/man/1/alien)

---

### Post by master_kernel on 2007-10-02
Use alien, as suggested by Pumalite. I believe it can convert many packages.

---

### Post by CSMatt on 2007-10-03
I thought alien only did RPMs.  It does tar.gz binaries too?

---

### Post by capink on 2007-11-03
If it is a pre-compiled binary you can convert it into deb using the command dpkg -b as follows:

1. Make a directory where you will extract the tar.gz, I will call it packagename. And inside this directory, create a subdirectory called DEBIAN. These two steps can be created using the following command:

```
mkdir -p ~/packagename/DEBIAN
```

2. Extract the contents of the binary into the directory you created in the previous step

```
cd ~/packagename && tar xvf /path/to/the/tar.gz
```

3. Create the control file of the package using the following command:

```
{ echo "Package: packagename";
echo "Priority: optional";
echo "Section: web";
echo "Maintainer: user <user@company.com>";
echo "Architecture: i386";
echo "Version: 1.0";
echo "Depends: package1, package2, .....";
echo "Description: Short Description";
echo " .";
echo " Long Description";
echo; } > ~/packagename/DEBIAN/control
```


4. Edit the control file using gedit or you favorite text editor

```
gedit ~/packagename/DEBIAN/control
```

replace the relevant values. If you know of any dependencies for the package add them to the dependency field. [COLOR="Red"]Otherwise, erase the dependency from the control file[/COLOR]. Make sure you preserve the format of the control file including newlines, spaces and dots.

5. Create the deb as follows

```
dpkg -b ~/packagename/ packagename.deb
```

---

