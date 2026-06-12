---
title: "How do I correct this Package Manager error"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-10-30
I am a "Senior Newbie" and I getting the following error message when I try to open the package manager:

  Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I am running Ubuntu 7.10

Your help will be appreciated.

---

### Post by taurus on 2007-10-30
Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by haldean on 2007-10-30
I would recommend doing what it says and running ```
sudo apt-get install -f
``` in the terminal ;)

That normally happens when you interrupt a package install or when you force a package to be installed without its dependencies. The command should fix it fine.

---

### Post by explorer716 on 2007-10-30
You have fixed my problem.  Thanks very much for your help.

---

