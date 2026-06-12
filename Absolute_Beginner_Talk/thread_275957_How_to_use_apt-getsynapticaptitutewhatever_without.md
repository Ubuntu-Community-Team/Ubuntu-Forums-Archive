---
title: "How to use apt-get/synaptic/aptitute/whatever without admin privileges"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by pedrorolo on 2006-10-12
Is there any way of using this programs without having admin privileges? Can't a user install programs with this applications in his user folders?
If not? why? This would be soo usefull!!

Example of use:

At my college there's Ubuntu installed on the workstations. Even so... there are a lot of applications that besides not beeing installed, they would be usefull for my work, but I don't feel like digging on their deps and installing all of them with dpkg in my local area... It would be perfect if there was a way of using synaptic/apt-get to install applications in users local area...

---

### Post by PriceChild on 2006-10-12
You MUST have admin privelages to alter anything you don't have privelages to.

On a standard system, you only own /home/<<username>>

To install packages from your home folder, you must firstly have admin privelages, and then may:
```
sudo dpkg -i <<name of package>>/deb
```

I hope this answers your question :)

---

### Post by Sirkent on 2006-10-12
Because of the way the packages work, they extract to the default location (not your user area). They wouldn't work properly if they were extracted anywhere else, because that's how the package has been built.

The only other way to install an application at a location of your choosing would be to compile it yourself.

(Anyone else feel free to correct me if I'm wrong).

---

