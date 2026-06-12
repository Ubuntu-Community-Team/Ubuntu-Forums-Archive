---
title: "Installation Trouble"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by JordanII on 2007-07-14
Earlier today I was trying to install Google Desktop for Linux with a .deb package. In the middle of the installation process the computer crashed (I had to many programs open). Anyway, now I am not able to install anything, even with apt-get. I went to upgrade Compiz in the terminal by following [this]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml") tutorial. This is what happened:


```

jordan@jordan-desktop:~/Desktop$ sudo apt-get -y remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-desktop-linux needs to be reinstalled, but I can't find an archive for it.
jordan@jordan-desktop:~/
```

I am running Ubuntu 7.04 Feisty Faun. What should I do? Thanks!



~Jordan

---

### Post by w4ett on 2007-07-14
Try re-installing GE...this should repair the broken dependency.

---

### Post by JordanII on 2007-07-14
> **w4ett said:**
> Try re-installing GE...this should repair the broken dependency.

What's GE? Thanks!


~Jordan

---

### Post by JordanII on 2007-07-14
If you meant GD I have no idea how to. Thanks for the help!


~Jordan

---

### Post by starsky on 2007-07-14
hi there :)
what does this do ?

$dpkg -C

(this checks for broken dependencies and suggests you how to get around it). :-D

Post back 

HTH

---

### Post by JordanII on 2007-07-14
> **starsky said:**
> hi there :)
what does this do ?

$dpkg -C

(this checks for broken dependencies and suggests you how to get around it). :-D

Post back 

HTH

Here is what I got:
```

jordan@jordan-desktop:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 google-desktop-linux
```

How should I go about reinstalling? Thanks!


~Jordan

---

### Post by w4ett on 2007-07-14
> **JordanII said:**
> What's GE? Thanks!


~Jordan

Google Earth

EDIT: sorry meant Google Desktop

---

### Post by JordanII on 2007-07-14
> **w4ett said:**
> Google Earth

The problem is with Google Desktop though. How should I reinstall it? Thanks!


~Jordan

---

### Post by w4ett on 2007-07-14
> **JordanII said:**
> Here is what I got:
```

jordan@jordan-desktop:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 google-desktop-linux
```

How should I go about reinstalling? Thanks!


~Jordan

 How did you originally attempt the Google desktop installation?  From the google website?....reinstall using the original method that you used..this should repair the apt-get fault.

---

### Post by starsky on 2007-07-14
do this -

$sudo dpkg -r google-desktop-linux

that should uninstall google desktop for linux
and then you can install whatever you like later on.

HTH.

as usual post back :)

---

### Post by JordanII on 2007-07-14
> **w4ett said:**
> How did you originally attempt the Google desktop installation?  From the google website?....reinstall using the original method that you used..this should repair the apt-get fault.

I tried to install with a deb package. I just double clicked on the downloaded deb and halfway through the installation process the computer crashed. I can't reinstall the original way because it tells me that a package manager is already open. There is no package manager that seems to be open so I can't close it. Thanks for the help!


~Jordan

---

### Post by JordanII on 2007-07-14
> **starsky said:**
> do this -

$sudo dpkg -r google-desktop-linux

that should uninstall google desktop for linux
and then you can install whatever you like later on.

HTH.

as usual post back :)

I got this:

```
jordan@jordan-desktop:~$ sudo dpkg -r google-desktop-linux
dpkg: error processing google-desktop-linux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 google-desktop-linux
```

Thanks for the help!


~Jordan

---

### Post by forestpixie on 2007-07-14
try to purge it 

```

sudo dpkg --purge google-desktop-linux
```

---

### Post by JordanII on 2007-07-14
> **forestpixie said:**
> try to purge it 

```

sudo dpkg --purge google-desktop-linux
```

I allready tried that. Anyway, I got it fixed with the command below:

```
 sudo dpkg -i google-desktop-linux_1.0.1.0060_i386.deb
```

Thanks for the help everyone!!!


~Jordan

---

### Post by starsky on 2007-07-14
anytime :)

---

