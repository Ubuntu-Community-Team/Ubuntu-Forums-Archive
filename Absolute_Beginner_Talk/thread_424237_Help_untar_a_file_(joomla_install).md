---
title: "Help untar a file (joomla install)"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2007-04-26
This is a really beginner question.  I am trying to untar something in my webserver (joomla).  

This is what I plan on doing.
cd /var/www
sudo wget [http://joomlacode.org/gf/download/frsrelease/111/263/Joomla_1.0.12-Stable-Full_Package.tar.gz](http://joomlacode.org/gf/download/frsrelease/111/263/Joomla_1.0.12-Stable-Full_Package.tar.gz)
sudo tar xvfz Joomla_1.0.12-Stable-Full_Package.tar.gz

I want to have the joomla folder look like this 
/var/www/NSCS/(joomla's contents)

Then, I think i need to change permissions, so i will do this.
sudo chmod 777 /var/www/NSCS

Does all of this seem right?  How do I make sure it is in that file folder

Thanks for the help,
Hans

---

### Post by hansoffate on 2007-04-26
Bump

---

### Post by annda on 2007-04-26
which steps have you already done? where are you stuck?

for chmodding, you might need the recursive option -r for all subdirectories.

here's more info:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by bashologist on 2007-04-26
I'm not sure of your conditions but I think you would need at least read and write for root. So this should be enough:

sudo chmod 600 /var/www/NSCS
cd /var/www
sudo wget [http://joomlacode.org/gf/download/frsrelease/111/263/Joomla_1.0.12-Stable-Full_Package.tar.gz](http://joomlacode.org/gf/download/frsrelease/111/263/Joomla_1.0.12-Stable-Full_Package.tar.gz)
sudo tar xvfz Joomla_1.0.12-Stable-Full_Package.tar.gz -C NSCS

---

### Post by hansoffate on 2007-04-26
Thanks for the help.  I did the chmod 600.  It didn't work.  I then did a chmod 777.  It somewhat worked.  Now when I got to the installer, it said everythign was UNWRITABLE.  i then did.
$ sudo chmod 777 -R /var/www/NSCS

Thanks for the help,
Hans

---

