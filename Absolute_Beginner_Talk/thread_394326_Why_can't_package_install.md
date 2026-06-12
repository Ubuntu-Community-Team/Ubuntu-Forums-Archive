---
title: "Why can't package install?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-03-26
I am trying to install libopenal0_0.2004090900-1.1_i386.deb through the package manager. All depedancies are installed and the green checkmark is lit. I click on it to install, and it goes to the little progress bar, but then it displays: 
Failed to install package 'libopenal0_0.2004090900-1.1_i386.deb'
I flip down the terminal window and it shows absolutely nothing. What's going on?

---

### Post by Cippa Lippa on 2007-03-26
what is that program supposed to do? sometimes packages do not install because they conflict with another program which is already running.

---

### Post by rouge568 on 2007-03-26
It's an audio library that I will use for Jahshaka.
On another note, when I try to install via terminal as root:

root@Home:/tmp# sudo apt-get install libopenal0_0.2004090900-1.1_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libopenal0_0.2004090900-1.1_i386.deb

---

### Post by STREETURCHINE on 2007-03-26
do you have all your repositories enabled.?

---

### Post by igknighted on 2007-03-26
If you have the package on your hard drive already then use "sudo dpkg -i libopenal0_0.2004090900-1.1_i386.deb".  If you are trying to install it from the repos, you don't need the versioning info or the arch.  Use: "apt-cache search libopenal" to find the proper package name and then install with apt-get when you find it.

---

### Post by rouge568 on 2007-03-26
Yes all repositories are enabled.

igknighted - I tried it and this came up:
> 
root@Home:~$ sudo dpkg -i /tmp/libopenal0_0.2004090900-1.1_i386.deb
dpkg: regarding .../libopenal0_0.2004090900-1.1_i386.deb containing libopenal0:
 libopenal0a conflicts with libopenal0
  libopenal0 (version 0.2004090900-1.1) is to be installed.
dpkg: error processing /tmp/libopenal0_0.2004090900-1.1_i386.deb (--install):
 conflicting packages - not installing libopenal0
Errors were encountered while processing:
 /tmp/libopenal0_0.2004090900-1.1_i386.deb



it seems to me that  "libopenal0a conflicts with libopenal0"  implies it is already installed. Yet when I try to install the Jahshaka package, it lists libopenal0 as a needed dependancy. However, it doesn't show up in the Package Manager lists.

---

### Post by zvacet on 2007-03-27
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libopenal0&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libopenal0&searchon=names&subword=1&version=edgy&release=all")

---

