---
title: "package rpm is not available"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Greedo on 2007-12-30
Hi, this is my first time at using linux for my home desktop / not using it on a server environment - so I'm not 100% clueless only about 95%, lol

I'm trying to get my printer going and I have downloaded the printer .rpm files and was going through the steps on one of the posts listed here but when I went to the terminal window to give my command rpm -Uvh MFC210Clpr-1.0.2-1.i386.rpm

then this is what I got:

```

The program 'rpm' is currently not installed.  You can install it by typing:
apt-get install rpm
bash: rpm: command not found
root@my-laptop:/home/my/Desktop# apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rpm has no installation candidate
root@my-laptop:/home/my/Desktop# 

```

how do I go about fixing this so I can install the printer drivers needed?

---

### Post by mick222 on 2007-12-30
Ubuntu does not use rpm packages go to system - administration-printers -add printer
should find and install drivers for your printer

---

### Post by aktiwers on 2007-12-30
Didn't they provide .deb downloads?

RPM is for Redhat and not debian based distros like ubuntu.

You can convert it to .deb with Alien:
```
sudo apt-get install alien
```Then cd to the folder you have the RPM file and:
```
alien -d yourRPMfile.rpm
```

EDIT:
Oh yes almost forgot, then go to the folder, find the new .deb file and double-click it.

---

### Post by markharding557 on 2007-12-30
ubuntu is not an rpm based disro,you need a deb,that and other info is available on these links
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html")
driver download(deb) here
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")
this thread may be useful too
[http://ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc210]("http://ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc210")

---

### Post by PeterJS on 2007-12-30
> **Greedo said:**
> 
```

The program 'rpm' is currently not installed.  You can install it by typing:
apt-get install rpm
bash: rpm: command not found
root@my-laptop:/home/my/Desktop# apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rpm has no installation candidate[/B]
root@my-laptop:/home/my/Desktop# 

```

In addition to all the rightly stated use deb not rpm posts above, the reason rpm doesn't install is that your sources.list file is broken. The installer makes some dumb assumptions about internet connectivity during the install process, specifically that if you don't have an active internet connection when installing you never will, so based on this it disables all the software repositories. To reactivate them go to System > Administration > Software Sources, and make sure that all 4 sections are enabled, the source entry down at the bottom is optional but worth making note of if you ever want it.

---

