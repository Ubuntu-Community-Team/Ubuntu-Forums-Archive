---
title: "RPM and TAR files for Vmware"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-15
Can someone tell me the difference between .tar.gz and .rpm files for Linux?  I am downloading Vmware for Linux (Ubuntu 7.10) and would like to know which file I should be downloading.  Thanks.

---

### Post by PeterJS on 2008-01-15
RPM is the Red Hat Package Management format. Alien can install RPM packages, but it's kinda dicey with the post install script. Tar.gz is pretty much the universal archive format (like rar, but from the old unix days). It probably contains the binaries and an installer script.

---

### Post by nikoPSK on 2008-01-15
tar, for compiling source code, rpm for redhat. There are debs for debian based systems. :)

---

### Post by Matt26 on 2008-01-15
Thanks for the replies- I don't know which i should be downloading for Ubuntu 7.10 as I am new to the OS... any suggestions would be greatly appreciated.

---

### Post by nikoPSK on 2008-01-15
For ubuntu generally it's source and debs. :)

---

### Post by PeterJS on 2008-01-15
Either would work, I'd start with the tar.gz first, it may be the less clean way of installing vmware, it doesn't add the package management metadata when it installs, but is more likely to work properly. RPM has the metadata, but the post install scripts are designed to work with red hat not ubuntu, so they *might* work, keyword being might.

---

### Post by Matt26 on 2008-01-15
what are debs?  the vmware site only has tar and rpm versions available for download- how should I proceed for installation?

---

### Post by nikoPSK on 2008-01-15
> **PeterJS said:**
> Either would work, I'd start with the tar.gz first, it may be the less clean way of installing vmware, it doesn't add the package management metadata when it installs, but is more likely to work properly. RPM has the metadata, but the post install scripts are designed to work with red hat not ubuntu, so they *might* work, keyword being might.

RPM is a bit "hard" too. The newest version came out a while ago. :)

> [B][SIZE=3]Command Line![/SIZE]
[/B]With so many things to install and so many ways to install them it's very easy to adapt to the the many ways. At the soul of every installation method they use the world renowned "Advanced Package Tool". The power of APT is overwhelming. Join us apt users, nothing comes close!

Why is apt so cool? (It has Super Cow Powers!) It was the first to actually handle dependencies in apps/ software. Other distributions of Linux like Red-Hat used RPM files with dependencies. Example: An RPM for say the gimp will require the graphical tool kit (gtk) which the gimp is based on. So If you tried installing the gimp RPM without the gtk RPM it would fail miserably. So you take the gtk RPM and try installing it.... gtk has dependencies on three other things and so on and so on until you can't find a certain RPM for one of the dependencies and you say (censored) that's enough and then walk away.

APT on the other hand is superior to RPM in every way mainly because it is designed to retrieve your dependencies. So if you want Inkscape it will retrieve all the dependencies as well as the package itself ensuring total simplicity. APT also includes installation resuming, which means if for some reason the install doesn't complete it will start where it left off next time.


---

### Post by nikoPSK on 2008-01-15
> **Matt26 said:**
> what are debs?  the vmware site only has tar and rpm versions available for download- how should I proceed for installation?

debs are debian install packages, just download them, and hit install. :)

---

### Post by PeterJS on 2008-01-15
Deb is the extension used by debain packages (and the shortened slang name for them), ubuntu being a debian derivative uses deb packages to install most things. Everything installed through apt (apt-get, aptitude, synaptic, update manager) comes in a deb, there's also a bunch of ubuntu debs over on getdeb.net (they're one of the best third party collection of loose debs). The tar.gz installer should be universal, it won't be ideal for any linux system but should be good enough for any system.

---

### Post by Matt26 on 2008-01-15
Forgive my confusion- i only have 2 options for download- the tar and rpm files.  so the rpm file is meant for other linux ditros like red hat... so what can i do with the tar file to install it in Ubuntu?  is this apt you mentioned a way of installing the tar file?  how can i go about installing the tar file?

---

### Post by nikoPSK on 2008-01-15
for installing a tar file you can read this:
[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

nikoPSK

(basically just, cd to the folder, ./configure, make, make install. :p)

---

### Post by PeterJS on 2008-01-15
Generally checkinstall is cleaner than make install. I can also tell you that vmware would never release a source package, so source install instructions aren't going to do you much good. But being a comercial product I can't imagine they wouldn't have a great README, or INSTALL doc in the root of the archive.

---

### Post by nikoPSK on 2008-01-15
> **PeterJS said:**
> Generally checkinstall is cleaner than make install. I can also tell you that vmware would never release a source package, so source install instructions aren't going to do you much good. But being a comercial product I can't imagine they wouldn't have a great README, or INSTALL doc in the root of the archive.

readme's are always useful, but generically it's those above steps mentioned.

---

### Post by zvacet on 2008-01-16
If you want to install vmware-server do it from synaptic.If you want to play with tar files [here it is](http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10).

---

