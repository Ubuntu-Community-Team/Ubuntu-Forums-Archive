---
title: "No GUI, Old World Mac sticks... *HELP*"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-07-27
I am attempting to install Ubuntu 6.10 on an Old World Apple Powerbook G3.  [I am using this guide: [http://http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/]("http://http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/").]

After completing the first part of the installation, I restart into the freshly installed OS.  However, when it is booting, it gets to the prompt "Running local boot scripts" and sticks.  I don't know how long it stays, but i let it sit there for quite some time.

I can press Enter and I am able to log in to the computer, however there is no GUI.  When I try to install or start the GUI, it does not work.

So: (Sorry for the long intro) how can I get everything to work the way it should?  I really just need the GUI it seems, or do I need to wait longer at "Running Local boot scripts" ?

Please help,

Thanks

---

### Post by Pragmatist on 2007-07-28
What do you get if you type:
```
ls /usr/sbin/gdm
```

---

### Post by mdknaebel on 2007-07-28
```
mike@ubuntu:~$ ls /usr/sbin/gdm
[COLOR="Lime"]/usr/sbin/gdm[/COLOR]
mike@ubuntu:~$
```

After I press Enter, log in and type that, it just shows up in green below what I just typed...

Thanks

---

### Post by Pragmatist on 2007-07-28
Good!  That means that GDM (Graphical Display Manager) is installed, which  almost certainly means that a GUI has been installed.  My initial guess is that it is an X configuration issue.  First, however, try this:

This next command will probably do nothing since GDM is probably not running. Nevertheless...
```
sudo /etc/init.d/gdm stop
```

Now start GDM and see if anything happens.
```
sudo /etc/init.d/gdm start
```

---

### Post by mdknaebel on 2007-07-28
Hmm... 

Well I type the first (or second), and my password and it says

> sudo: /etc/init.d/gdm: command not found

Any Ideas?

---

### Post by yorkie on 2007-07-28
try typing

sudo dpkg-reconfigure gdm

---

