---
title: "Nvidia Driver"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2007-09-25
How do i remove envy and all its sub stuff, and how do i remove the NVIDIA driver i installed manuly ?

---

### Post by ThRixXx on 2007-09-25
?

---

### Post by chrisxp on 2007-09-25
try "apt-get remove envy" and then "apt-get autoremove" to remove the associated files/packages..

for the nvidia driver, i dont know, sorry

---

### Post by Hospadar on 2007-09-25
I would first use envy to remove the nvidia drivers you installed manually.  there is really not other easy way I know of to remove them.  If you do the "completely remove" and "clean" options from within envy, this will get rid of the manually installed drivers.  You may then use envy to install the repository drivers (as the above choices will again remove those as well0 and then proceed to do what chrisxp suggests to remove envy.

Just so you know, the "sudo apt-get autoremove" removes any packages that were installed as a dependancy of a package which is no longer installed itself

Also note, you'll have to prepend "sudo" to chrisxp's commands.
 (unless you are logged in as root, which is not really a good idea)

---

