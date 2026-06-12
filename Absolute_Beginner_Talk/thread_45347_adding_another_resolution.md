---
title: "adding another resolution?"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-29
I accidentally did not select my resolution (1280x1024) at install so how do I add it? I have searched the forums and it looks like I should add that mode to xorg.conf but I have loaded terminal and done "gedit xorg.conf" and it just gives me a blank file. Do I have the path wrong?

---

### Post by Leif on 2005-06-29
If you want to edit it by hand the line is "sudo gedit /etc/X11/xorg.conf", otherwise try "sudp dpkg-reconfigure xserver-xorg"

---

### Post by gammyhand on 2005-06-30
[QUOTE=Leif]If you want to edit it by hand the line is "sudo gedit /etc/X11/xorg.conf", otherwise try "sudp dpkg-reconfigure xserver-xorg"[/QUOTE]
 The first suggestion gives me a blank file and the second one says:

ralph@ralph:~ $ sudo dpkg-reconfigure xserver-xorg
Package `xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed


P.S - very irriratingly control+c and control+v don't work in terminal :(

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]The first suggestion gives me a blank file and the second one says:

ralph@ralph:~ $ sudo dpkg-reconfigure xserver-xorg
Package `xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed


P.S - very irriratingly control+c and control+v don't work in terminal :([/QUOTE]


try this command please:

> sudo apt-get install ubuntu-desktop

---

### Post by gammyhand on 2005-06-30
[QUOTE=poofyhairguy]try this command please:[/QUOTE]
 It says:

Reading Package Lists... Done
Building Dependency Tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]It says:

Reading Package Lists... Done
Building Dependency Tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.[/QUOTE]


I just thought- you are using Warty correct? Dumb me...that is a Hoary command. Try this instead:

sudo dpkg-reconfigure xserver-xfree86

---

### Post by gammyhand on 2005-06-30
[QUOTE=poofyhairguy]I just thought- you are using Warty correct? Dumb me...that is a Hoary command. Try this instead:

sudo dpkg-reconfigure xserver-xfree86[/QUOTE]
 Thanks. I have left the Hoary 32bit install cd downloading while I am at work though so will be installing that when I get home. Hopefully I will finally get a working linux :)

---

