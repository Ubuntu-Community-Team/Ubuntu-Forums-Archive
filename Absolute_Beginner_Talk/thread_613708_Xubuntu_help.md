---
title: "Xubuntu help"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-11-15
When installing vmware it asks me this:

What is the location of the directory of C header files that match your running
kernel? 

Whats the location?

thanks

---

### Post by Pabx on 2007-11-15
anyone?? plz

---

### Post by kast on 2007-11-15
[B]/usr/src/CurrentKernel/include
[/B]
Current Kernel  can be found with the **uname -r**. Command

---

### Post by kast on 2007-11-15
If that directory is missing then you dont have the Headers installed for your current Kernel, so use the 
**uname -r** command and find the kernel version you have and then you can run 

**sudo apt-get install linux-headers-<version>**        <~~ thats the info you get from **uname -r**

---

### Post by Pabx on 2007-11-15
Thank you !

---

### Post by kast on 2007-11-15
Anytime!

---

