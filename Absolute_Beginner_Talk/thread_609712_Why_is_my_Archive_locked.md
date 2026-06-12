---
title: "Why is my Archive locked?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by jonpon on 2007-11-11
I had a crash and keep geting this error

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

can anyone tell me what it means and better, how to fix it!

when I do this
sudo apt-get -f install
I get this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-pycurl python-pyrex
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
jonpon@jonpon-laptop:~$

Can anyone please help.

---

### Post by Pumalite on 2007-11-11
Is Synaptic closed?

---

### Post by jonpon on 2007-11-11
Yes,The only thing open is this firefox and terminal.

---

### Post by Pumalite on 2007-11-11
Find out which one this is: 1 not fully installed or removed.
And remove it with this:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

