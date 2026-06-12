---
title: "How do I fix this error message?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-12-28
I get the following error message when I try to update my system.

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)


How do I fix this?

---

### Post by Dr. Nick on 2005-12-28
look at your /etc/apt/sources.list file and make sure their are no spaces in the url. It looks like their is a space or other error in one line.

If you dont see one post the terminal output of 
sudo cat /etc/apt/sources.list
for others to look at

---

