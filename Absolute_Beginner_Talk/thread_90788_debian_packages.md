---
title: "debian packages?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by andy101 on 2005-11-15
I was just wondering whether debian packages will work on ubuntu or not?
the files in /ubuntu/pool/ all have .deb extensions.

Also is it possible to download the .deb files and install them by hand? My linux machine has no internet so I can only download from a differant machine

also archive.ubuntu.com lists packages with things like 2ubuntu1 and 9ubuntu4 at the end, what are these for and how do I know which one to use?

Thanks

---

### Post by Kyral on 2005-11-15
Everything in Apt-Get is a debian package. Apt-Get is basically an easier way to utilize the Debian Package.

Yes you can download them by hand but make sure that you snag everything it depends on (and what they depend on and etc, this is why Apt-Get was made ;P)

As for the versioning, its all about Debian and Ubuntu. The first number is the "Debian Revision", the revision that Debian made to the package if any (a leading 0 means that it never came from Debian). The ubuntu<number> is the Ubuntu Revision. Basically it comes from when Debian and Ubuntu have to fix minor bugs in packages.

---

### Post by Manny C on 2005-11-15
[quote=andy101]I was just wondering whether debian packages will work on ubuntu or not?
the files in /ubuntu/pool/ all have .deb extensions.[/quote]
Yes they will work, provided that you also have the dependencies installed.
[quote=andy101]
Also is it possible to download the .deb files and install them by hand? My linux machine has no internet so I can only download from a differant machine
[/quote]
Say you download the debian package foo.deb. Then to install this you simply issue the following command in a terminal/konsole in the directory where the *.deb file is saved:
```
 sudo dpkg -i foo.deb 
```
For further information about the dpkg command, read the manual:
```
 man dpkg 
```

[quote=andy101]
also archive.ubuntu.com lists packages with things like 2ubuntu1 and 9ubuntu4 at the end, what are these for and how do I know which one to use? Thanks[/quote]

Good question. I don't know the answer.

---

### Post by az on 2005-11-15
[QUOTE=andy101]I was just wondering whether debian packages will work on ubuntu or not?
[/QUOTE]

Yes and no.  Some debian packages have debian-specific tweaks.  Some ubuntu packages have ubuntu-specific tweaks.  Some are built with different libc6 versions.  It is best to stick with packages from your own distribution.  They are all compatible on the source code level, so you can always build them yourself - that is what backports are.

[QUOTE=andy101]
also archive.ubuntu.com lists packages with things like 2ubuntu1 and 9ubuntu4 at the end, what are these for and how do I know which one to use?

Thanks[/QUOTE]
It is really difficult to manage these packages without apt.  You are best to 
apt-get -d (packages)
which only downloads the packages and their dependancies and then move the pile of packages you just downloaded to the other machine.  Is this a possibility?

---

