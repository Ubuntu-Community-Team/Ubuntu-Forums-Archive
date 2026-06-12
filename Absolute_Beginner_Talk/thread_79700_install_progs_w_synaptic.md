---
title: "install progs w/ synaptic"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by pperk97 on 2005-10-20
i've installed a couple progs through synaptic but i don't see them in the menus.. i've rebooted and refreshed and they show in synaptic as being there but not in the menus...????

---

### Post by Kyral on 2005-10-20
Some programs don't create GNOME Menu entries (Like command line based ones). There IS a program you can install to create a "catch all" menu.

Fire up Synaptic and find and install "menus"

or

Fire up the Terminal and enter this

```
sudo apt-get install menus
```

However you do it, you'll need to open a terminal when its installed and issue this command

```
update-menus
```

Then just refresh the GNOME Panel and it SHOULD show up (As the Debian Menu)

---

### Post by oldmanstan on 2005-10-20
I tried doing that and it couldn't find a package called "menus"

---

### Post by darkmatter on 2005-10-20
```
sudo apt-get install menu
```

He made a typo;)

---

### Post by pperk97 on 2005-10-21
hmmmm, didn't seem to work.. do i need to be in a certain dir to run it..??? this is what it says;
pat@ubuntu:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree... Done
Package menu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package menu has no installation candidate

---

### Post by Gustav on 2005-10-21
The package is in universe repository you'll have to add it to your /etc/apt/sources.list.

Here's some informormation on how to do that [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

