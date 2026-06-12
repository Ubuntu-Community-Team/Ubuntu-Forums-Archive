---
title: "Complete Beginner to ubuntu"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by vanderlt on 2007-12-16
I have d/l and installed ubuntu 7.1 server on my dell 1950 quad core sata raid server. it appears to be a text based system, not that i am opposed to that (i am a netware user) but don't know what steps to take to make the server a basic web server and ftp server. Any ideas? Did i install the wrong version of linux? Any help would be greatly appreciated.

---

### Post by macogw on 2007-12-16
Servers are pretty much always text-based, except in the Windows world because Microsoft is weird.

Installing programs in Ubuntu uses Debian's package manager, apt.
```
sudo apt-get install <program>
```
so to get OpenSSH-Server (provides ssh and sftp), you'd do
```
sudo apt-get install openssh-server
```
(package names are always lowercase)

To get a LAMP (linux, apache, mysql, php) server setup, you can use tasksel, which selects packages by task.
```
sudo tasksel install lamp-server
```
To see other tasks tasksel offers, you can just run ```
sudo tasksel
``` and you'll get a nice ncurses UI in your terminal letting you mark off what you want.


Oh, and it's 7.10.  7 = 2007, 10 = October

---

### Post by fatality_uk on 2007-12-16
> **vanderlt said:**
> I have d/l and installed ubuntu 7.1 server on my dell 1950 quad core sata raid server. it appears to be a text based system, not that i am opposed to that (i am a netware user) but don't know what steps to take to make the server a basic web server and ftp server. Any ideas? Did i install the wrong version of linux? Any help would be greatly appreciated.

Are you looking to install a GUI onto your server?

Quick and dirty method ```
sudo apt-get install ubuntu-desktop
``` or install a desktop version of Ubuntu. The server version is to all intents and purposes Ubuntu, just without the GUI

---

### Post by Paqman on 2007-12-16
I thought you could select a nice guided LAMP set up during the server install?

---

