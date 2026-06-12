---
title: "Can't install/uninstall software due to error"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by duncan_nz on 2007-02-22
Everytime I try to install or uninstall some software, I get this crazy error...

[PHP]grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

Any idea on how to fix it?

---

### Post by scrooge_74 on 2007-02-22
Explain the steps you are taking to install or uninstall software

---

### Post by duncan_nz on 2007-02-22
Well, I go to synaptic for example and try to install something, such as wine for example, or if I go to console and use 

[PHP]sudo apt-get upgrade
sudo apt-get install[/PHP]

Or if I use "Applications>Add/Remove" Then I will get that error, it doesnt matter what method I use I get that darn error!

---

### Post by scrooge_74 on 2007-02-22
so doing 

sudo apt-get update
sudo apt-get install wine

does not work, do you have the repositories enable?

---

### Post by duncan_nz on 2007-02-22
That was just an example, getting wine, I was trying to build wine from source so I tried to install Git so I could get the very latest files for 0.9.31 to compile etc.

That was when the problem began, after I installed Git. Now I try to remove it, or I reinstall it etc and I get that error

but, yes all the repositories are enabled.

---

### Post by scrooge_74 on 2007-02-22
Can't be of much help to you anymore, for next time did  you try using the repository for wine from winehq?

---

