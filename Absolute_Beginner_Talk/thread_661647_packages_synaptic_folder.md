---
title: "packages synaptic folder"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by observ8 on 2008-01-08
i am very new to linux enviroment and i like to ask something

when i install a package through synaptic the package-s is downloaded and then installed
are there files or folders after the installation that i don't need anymore??
in which path can i find it ?? should i delete thhese files-folders???

---

### Post by Anicka on 2008-01-08
The packages are saved in /var/cache/apt/archives You can in principle delete the packages after download, but it can be handy to have them. What you can do is to run the command "sudo aptitude autoclean" it will delete any obsolete packages that you have or "sudo aptitude clean" it will delete all packages from the cache.

---

### Post by observ8 on 2008-01-08
> **Anicka said:**
> The packages are saved in /var/cache/apt/archives You can in principle delete the packages after download, but it can be handy to have them. What you can do is to run the command "sudo aptitude autoclean" it will delete any obsolete packages that you have or "sudo aptitude clean" it will delete all packages from the cache.

thank you for your answer, and a last question
why it is handy to have them? how should i use it

---

### Post by cerealtx on 2008-01-08
in case u have any probelms with the programs u can always reinstall quickly without having to re-dl

---

