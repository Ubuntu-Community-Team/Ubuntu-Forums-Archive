---
title: "upgrading to breezy"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-09-17
If I wanted to upgrade to breezy would I have to do a clean install?  Is there a way to keep all your programs and settings when installing breezy?  How would I install breezy?

---

### Post by aysiu on 2005-09-17
Change your /etc/apt/sources.list from hoary to breezy
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by XDevHald on 2005-09-17
[QUOTE=racermike1967]If I wanted to upgrade to breezy would I have to do a clean install? Is there a way to keep all your programs and settings when installing breezy? How would I install breezy?[/QUOTE]
You can most deffinently do an upgrade, but please note that Breezy Badger is not FULLY stable. So you will be at risk if you install and things do not go well. It's also a time project in which bug reporting will be needed to help improve it's state of progress so when the new release comes out, it will be stable enough to install.

All of your applications WILL still be there if you upgrade from your terminal window.

First open terminal,
> sudo gedit /etc/apt/sources.list - Replace all **hoary** with ***breezy***
Second: sudo apt-get update -  sudo apt-get upgrade Then install from there and it will upgrade for you.

Good Luck!

---

### Post by UbuWu on 2005-09-17
And make sure you have the ubuntu-desktop package installed before upgrading.

---

