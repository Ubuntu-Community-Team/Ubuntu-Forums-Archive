---
title: "[SOLVED] Could someone please tell me what this message means regarding emesene?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-02-27
emesene APT repository

add the following lines to your /etc/apt/sources.list


deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

Am I supposed to put this in a terminal or something??

Thanks

---

### Post by mister_pink on 2008-02-27
/etc/apt/sources.list is a text file containing a list of all your software sources. To edit it, go to a terminal and type:
gksudo gedit /etc/apt/sources.list

Add those lines to the end and save, then continue with whatever instructions you were following before.

Edit: I see their instructions dont actually go any further. So, next type in a terminal
sudo apt-get update
sudo apt-get install emesene

---

### Post by psam3 on 2008-02-27
Thank you

---

