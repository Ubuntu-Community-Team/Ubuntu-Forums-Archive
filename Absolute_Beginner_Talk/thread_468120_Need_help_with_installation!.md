---
title: "Need help with installation!"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-08
I've recently attempted to install Enlightenment 16, to no avail. I have no internet, so I just go online and download any packages I need. So I download "enlightenment_0.16.7.2-5_i386.deb" and used dpkg to install it, and I get something about needing "enlightenment-data", so I download "enlightenment-data_0.16.7.2-5_i386.deb" and try, it installs. So I go back and fourth with the package/dependency thing until I get to "Error: Dependency not satisfiable: libc6". I tried everythiing I could, older version and newer versions, no dice. It was either "A later version is already installed" or "Conflict with package tzdata". So out of desperation I type in "sudo dpkg -r --force-depends libc6". It uninstalled Libc6, and hosed the system. I am now installing Feisty, and I want to know:

1. Can you tell me a nice, step-by-step guide to installing Enlightenment? 

2. Does Feisty still have these tormenting conflicts between libc6 and tzdata? 

Note: I won't be replying for now - have to shutdown PC due to storm, power is faltering. :(

---

### Post by dmfield on 2007-06-08
there is a good [enlightenment tutorial]("http://ubuntuforums.org/showthread.php?t=20216&highlight=e17") on the forum might help ? let me know

---

### Post by shamushand on 2007-06-08
Thanks for the reply, but two problems - that requires internet, and all those links are down. Any other ones?

---

