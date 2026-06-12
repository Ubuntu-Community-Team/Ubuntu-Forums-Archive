---
title: "How to install programs"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by percival95 on 2006-02-02
Hi all!

I am just now exploring Linux. My question is how do you install a package file?

---

### Post by Perfect Storm on 2006-02-02
You can download (most) program through apt-get. eg: sudo apt-get install XXXXXXX or go to synaptic package manager.

If you found a .deb package on a site:
sudo dpkg -i XXXXXXXXX.deb

---

### Post by Madpilot on 2006-02-02
Here's a couple of pages to get you started:
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-02-02
Or see the second link of my signature.

---

### Post by percival95 on 2006-02-02
Thanks to all, now how do I uninstall a program?

---

### Post by Mickey1 on 2006-02-02
in synaptic uncheck the box of the application name and apply
it should be uninstalled for you

It's how i've been doing it

---

### Post by carlosqueso on 2006-02-02
or in a terminal ```
sudo apt-get remove <package name>
``` incidentally, both methods also work for programs installed via dpkg.

---

