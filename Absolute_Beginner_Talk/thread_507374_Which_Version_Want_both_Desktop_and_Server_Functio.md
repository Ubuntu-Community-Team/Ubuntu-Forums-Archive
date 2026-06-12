---
title: "Which Version? Want both Desktop and Server Functionality"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Peter108 on 2007-07-22
First post. ):P Am looking to migrate an existing x86 laptop off  WinXP onto Ubuntu, and to use the newly-configured machine for both personal/home use (i.e., office/desktop functionality), and to set up the server functionality in order to access Subversion version control software via http and in general to ramp up sysadmin skills for eventual professional use.

The [_Ubuntu download page_]("http://www.ubuntu.com/getubuntu/download") shows a desktop version and a server version.  Does the server version come without a desktop GUI?  Do I need to get the server version then install GNOME?  Definitely want the LAMP functionality.  What the way to go here given my goals?   Thanks.  Peter

---

### Post by be4truth on 2007-07-22
Sever edition has no GUI but can be installed afterwards if you want or need

---

### Post by 5-HT on 2007-07-22
> **Peter108 said:**
>   Do I need to get the server version then install GNOME?  Definitely want the LAMP functionality.

Easiest way would be to build up from the LAMP setup. You can then add on the desktop functionality (with GNOME, and all apps installed in the desktop install) using one command:```
sudo apt-get install ubuntu-desktop
```
cheers,

---

### Post by be4truth on 2007-07-22
Sever edition has no GUI but can be installed afterwards if you want or need

---

