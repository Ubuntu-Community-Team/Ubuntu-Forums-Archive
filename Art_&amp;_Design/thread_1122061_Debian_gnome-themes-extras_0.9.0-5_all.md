---
title: "Debian gnome-themes-extras_0.9.0-5_all"
date: 2009-04-10
forum: Art &amp; Design
---

### Post by showgun22 on 2009-04-10
I just tried Debian on my old PC for fun and I saw their gnome-themes-extras_0.9.0-5_all and I must say I really like the themes include in that package.
 
I would like to know if there is a way to install them on Ubuntu?
If so I would appreciate a small howto for this keep in mind I am no expert
Thanks

---

### Post by Therion on 2009-04-10
Download, save and install this .deb file:

[http://ftp.debian.org/debian/pool/main/g/gnome-themes-extras/gnome-themes-extras_0.9.0-5_all.deb](http://ftp.debian.org/debian/pool/main/g/gnome-themes-extras/gnome-themes-extras_0.9.0-5_all.deb)

---

### Post by dje on 2009-04-10
i did not want to install the debian package in case of breakages..

download the package from the [debian package site]("http://packages.debian.org/lenny/all/gnome-themes-extras/download")
in a terminal:
```
cd /path/to/location/of/deb
mkdir gnome-themes-extras
dpkg -x gnome-themes-extras*.deb gnome-themes-extras
```
then navigate to this directory and go through it (/gnome-themes-extras/usr/share), you can drag and drop the directories under /icons and /themes into System >> Preferences >> Appearance to install them ;)

dje

---

### Post by howefield on 2009-04-10
That looks like an old package, the list can be found here

```
http://ftp.debian.org/debian/pool/main/g/gnome-themes-extras/
```

Download the latest deb package, you would probably want

```
gnome-themes-extras_2.22.0-3_all.deb
```

then double click the downloaded file and follow the instructions to install.

---

### Post by showgun22 on 2009-04-10
Sorry about my lack of knowledge 

1) I had already downloaded the file and the deb installer does not install anything from what I can see all you can do is extract
2) I also extracted to its own folder I had also tried System >> Preferences >> Appearance to install them but no luck on how to do it

3) I just copied the directories to where they should be in the usr/share but every time I use Preferences >> Appearance to change the theme it does change
 a few things but not all I get this error

the theme will not look as intended because the required GTK+theme engine smooth is not installed

sounds like it might be a lost cause

Thanks

---

### Post by balaknair on 2009-04-18
Open Synaptic> search for 'gtk engines smooth'> install

---

