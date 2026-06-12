---
title: "Problem installing automatix on Ubuntu 7.04"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-15
I downloaded automatix, but when the package installer opened, it gave an error message:

"Error: Dependency is not satisfiable: python2.4"

What does it mean?

Until I fix this, the package installer will not install automatix.

---

### Post by reidms on 2007-05-15
I believe you need to install Python 2.4 mate

---

### Post by swarup on 2007-05-15
> **reidms said:**
> I believe you need to install Python 2.4 mate

Thanks!  --I had no idea what that meant. 

I assume I can just google "python 2.4" and that should get me the needed item."

---

### Post by icechen1 on 2007-05-15
> **swarup said:**
> Thanks!  --I had no idea what that meant. 

I assume I can just google "python 2.4" and that should get me the needed item."

You could just download it with synaptic package manager.

---

### Post by bobplano on 2007-05-15
yea, ubuntu is different from windows in that way. instead of browsing the internet and finding possibly shady sites that have the software you want, almost everything you want/need is in the repositories, and since most of them are in ubuntu repostitories they can be trusted

---

### Post by reidms on 2007-05-15
Yes, just open Synaptic Package Manager under System and check Python 2.4

A dependency is something required by another program to function correctly

---

### Post by swarup on 2007-05-15
> **reidms said:**
> Yes, just open Synaptic Package Manager under System and check Python 2.4

A dependency is something required by another program to function correctly

As soon as you told me I needed to download python 2.4, I went to the Python website and downloaded it. Actually the site is up to python 5.1 and they recommended that as better, so I downloaded it. But because I haden't seen all your (two or three people's) replies that I should do it using synaptic package manager, so now I've downloaded it on my own and I don't know what to do next. I unzipped the download and have it in a folder in my computer. Now how to I install it? Can I use the synaptic package manager now to install it???

---

### Post by mstlyevil on 2007-05-17
> **swarup said:**
> As soon as you told me I needed to download python 2.4, I went to the Python website and downloaded it. Actually the site is up to python 5.1 and they recommended that as better, so I downloaded it. But because I haden't seen all your (two or three people's) replies that I should do it using synaptic package manager, so now I've downloaded it on my own and I don't know what to do next. I unzipped the download and have it in a folder in my computer. Now how to I install it? Can I use the synaptic package manager now to install it???

Automatix normally installs python 2,4 for you during the installation. If it fails try this command first.

```
sudo apt-get -f install
```

If that does not work then you can install it using synaptic. You should never install a package from the maintainers web site if it is available in the repos. 

If you need further help with Automatix please visit us at the [Automatix Forums]("http://www.getautomatix.com/forum/").

---

### Post by egoldtech on 2007-06-16
I had the same problem right after installing 7.04, 
as soon as i made the updates, after trebooted, there were no more problems with python2.4 ( there were an update in python that was necessary).
regards

chek for updates !!!

---

### Post by kvorion on 2007-06-16
You could install automatix directly from synaptic instead of installing python first and then installing automatix. The best part of synaptic is that it resolves all your dependencies.

---

### Post by GoPool on 2007-07-03
Just update software sources after you install ubuntu. That should resolve the issue.

---

### Post by ajmorris on 2007-07-03
i dont advise that you install automatix. Automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu. its just not worth breaking your system over :)

---

### Post by Vajra Vrtti on 2007-07-03
The only thing I installed using Automatix was multimedia codecs, which works fine and are tricky for beginners. After that I uninstalled Automatix because most things it installs are quite ease to install without it.

---

