---
title: "How do i find source.list"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by kittycatsexycat on 2006-03-11
How do i get to my source list to edit it...:-k 

:cool:

---

### Post by bluevoodoo1 on 2006-03-11
sudo gedit /etc/apt/sources.list

---

### Post by kittycatsexycat on 2006-03-11
nice one hopefully that should work

:KS

---

### Post by kittycatsexycat on 2006-03-11
Nah that didn't solve it...

The problem is is that when i update it cant because gnome-session doesn't work or something...

It says this to me...

root@ubuntu:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-session (2.13.92-0ubuntu4) ...
mv: accessing `/etc/alternatives/x-session-manager.1.gz': Permission denied
update-alternatives: unable to install /etc/alternatives/x-session-manager.1.gz.dpkg-tmp as /etc/alternatives/x-session-manager.1.gz: Permission denied
dpkg: error processing gnome-session (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-session
E: Sub-process /usr/bin/dpkg returned an error code (1)

I thought all of it might help... :D

---

### Post by aysiu on 2006-03-11
As I understand it from your other thread, you're trying to do a dist-downgrade from Dapper to Breezy. I said in that other thread that it will most likely **not** work, as I don't believe there's any utility in apt-get that allows you to favor previous versions of applications over new ones (you can choose not to upgrade, but I don't think you can actually downgrade the package).

Honestly, your best bet is to stick with Dapper until its official release or do a clean reinstall of Breezy.

---

### Post by bluevoodoo1 on 2006-03-11
What are you trying to do exactly? From your other threads it seems you are trying to downgrade back to breezy? Although it's been suggested that it might not be able to be done.

---

