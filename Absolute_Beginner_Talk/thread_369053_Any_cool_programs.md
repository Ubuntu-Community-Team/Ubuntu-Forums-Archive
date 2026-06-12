---
title: "Any cool programs?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by pwrntspd on 2007-02-24
so i just installed Xubuntu yesterday...and i was wondering if there are any cool programs i should check out.  Its just an old pc that im screwing around with so im not worried about messing it up. Any suggestions?

---

### Post by FyreBrand on 2007-02-24
In the menu there is an add/remove programs application.  It will show you all the programs you can install.  If you computer can handle it you could install Open Office, GIMP, games, or any other program on the list.

You might need to modify your sources.list and add repositories to get more applications.  You should be able to do that from the add/remove programs app or if you're comfortable with an editor you can modify the file directly.

Here is my basic sources.list with common repositories:
```
## Main
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major Bug Fixes
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Universe && Multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Backports
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## Canonical Commercial
deb http://archive.canonical.com/ubuntu edgy-commercial main
```
This is for Edgy Eft 6.10 (any flavor Kubuntu, Ubuntu, Xubuntu).  If you use Dapper then change all the instances of Edgy to Dapper.

This gives you the full range of applications from Ubuntu repositories.  If you are looking for a specific type of app post back and we can search for one.

---

### Post by pwrntspd on 2007-02-24
sweet thanks fyre

---

