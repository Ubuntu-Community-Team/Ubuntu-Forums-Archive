---
title: "Joomla!"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2007-12-20
Hello again,

I was wondering is there a step-by-step install guide of Joomla.  Also -> as I've never used it before could someone please point me to a great tut for it?  Thank you!

---

### Post by Xiong Chiamiov on 2007-12-21
Joomla's a CMS.  You're installing on a local web server, or a remote one?  I'm not sure what that has to do with ubuntu...

---

### Post by indytim on 2007-12-21
I just completed a Joomla install on my local server.  Basically:
1.  Build a LAMP installation (I'm running mine on Kubuntu 7.10).
2. Download the Joomla install (I used the .tar.gz package).
3.  Either set up a new directory WITHIN you web server, or you can elect to install Joomla directly at the root of the web server (/var/www).
4.  Unpack the Joomla to it's destination directory.
5.  Start the install application by accessing the main index file like
```
http://localhost/joomla/index.php
```
6.  Fill in the fields for the installation and follow the instructions.  Should be off an running then.

If your installing is on a public web site that is hosted, check with your hosting service as a number of them offer Joomla as a optional install to the site (mine did).

Have Fun,

IndyTim

---

