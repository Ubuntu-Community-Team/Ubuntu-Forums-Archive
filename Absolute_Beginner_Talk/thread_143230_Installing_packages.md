---
title: "Installing packages"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by lkvee on 2006-03-12
I'm trying to get WiFi quickly set up, and I wanted to install not only the ndiswrapper package, but also the ndisgtk package.

I had no problem with ndiswrapper, but since ndisgtk was not on the Breezy CD, I went to [http://packages.ubuntu.com/breezy/net/ndisgtk](http://packages.ubuntu.com/breezy/net/ndisgtk) to fetch it.   I downloaded it, put it on a floppy, mounted the floppy, and tried and tried and tried.  Then I tried again on a CD-R.  Synaptic seems to have trouble recognizing that what I had on that CD (and floppy) was a package I wanted to install.

I suspect what I'm asking's an FAQ, and I'm going to read up on a few other sites for answers, but I'd love to hear about the things I overlooked when I tried to install ndisgtk.

Thanks for reading!

---

### Post by Mustard on 2006-03-12
Deb files that you want to install locally are installed with the dpkg command.

```
sudo dpkg -i packagename.deb
```

-edit-

Installing this way you might hit some dependency problems (missing packages).  If you do then download those packages that it says it needs and install them too.

Looking at its description shows a few dependencies. Some might be installed already though.

```
mustard@slave:~$ apt-cache show ndisgtk
Package: ndisgtk
Priority: optional
Section: universe/net
Installed-Size: 104
Maintainer: Sam Pohlenz <retrix@internode.on.net>
Architecture: all
Version: 0.5-1ubuntu1
Depends: ndiswrapper-utils, python, python-gnome2
Filename: pool/universe/n/ndisgtk/ndisgtk_0.5-1ubuntu1_all.deb
Size: 11134
MD5sum: f7dead9cfd1f3bc40c425fa41e66886b
Description: graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
 ndisgtk is a GTK based frontend for ndiswrapper, allowing an easy way to
 install Windows wireless drivers.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by AtinLango on 2006-03-12
[QUOTE=lkvee]Synaptic seems to have trouble recognizing that what I had on that CD (and floppy) was a package I wanted to install.[/QUOTE]

If synaptic fails, why not try dpkg?

---

