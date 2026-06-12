---
title: "administrative problem...."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-08
my os --->ubuntu 7.04
in terminal
------------------------------------------------------
myname@ubuntu7.04:~$ sudo -i
>>> sudoers file: syntax error, line 17 <<<
sudo: parse error in /etc/sudoers near line 17
myname@ubuntu7.04:~$
----------------------------------------------------
how to solve this error.....
and i can't open any other administrative action (System->Administration->...,)



pls help

---

### Post by Celegorm on 2007-10-08
There is a syntax error in /etc/sudoers. If by any chance you have enabled root, log into root and run ```
visudo
``` in the terminal to edit /etc/sudoers. Otherwise try booting up with the ubuntu live cd, and editing /etc/sudoers from there (look for the file wherever the live cd mounts the partition in which you have ubuntu installed, it might be something like, for example, /media/disk/etc/sudoers). Look for a syntax error near line 17, or if you don't know what to look for, post the contents of /etc/sudoers here.

edit- Hard drive partitions are not mounted by default in the live cd, but if you double click a disk on the desktop, which will open it up in the file browser, it will become mounted under /media/disk, and if you double click a second one it will mount under /media/disk-1 (unless the ubuntu live cd is vastly different from the xubuntu one that I tried it with). Also you will need to edit the file as root, so use something like 'sudo nano /media/disk/etc/sudoers' in the terminal. I don't believe you will need to enter a password for this.

---

### Post by mokkai on 2007-10-08
fine, i got it.

thank you man...

---

