---
title: "How to install SDL packages."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by kandza on 2008-01-05
I am a total newbie on linux and wanted to install a game called wesnoth. For that i need some libraries. But if i want to install them in need SDL packages.How do i do that?:confused:

---

### Post by p_quarles on 2008-01-05
They should be installed automatically, if Wesnoth depends on them. Will it not let you proceed?

Try running this (first press alt-F! to open a terminal):
```
sudo apt-get install wesnoth
```
If you confirm the installation, everything you need should automatically install itself.

---

### Post by kandza on 2008-01-06
When i do that it says: Couldn`t find package wesnoth. But i downloaded it.

---

### Post by arvindenrique on 2008-01-06
did u paste it in the desktop? if placed try now.

---

### Post by kandza on 2008-01-06
i tried it then i extracted it but it says the same

---

### Post by arvindenrique on 2008-01-06
use this command



sudo apt-get install wesnoth


place the folder in the desktop and use this command

---

### Post by Perfect Storm on 2008-01-06
First; You don't need to compile SDL or wesnoth, you can get them via synaptic. (system tab ---> Administration ----> synaptic). 
If you don't have internet access on Ubuntu you can get the Ubuntu packages on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Download them to your Desktop;

```
cd ~/Desktop
sudo dpkg -i <name-of-package>.deb
```

or doubleclick it the package.

---

### Post by Perfect Storm on 2008-01-06
> **arvindenrique said:**
> use this command



sudo apt-get install wesnoth


place the folder in the desktop and use this command

Wrong commands to install manually downloaded Ubuntu packages.

---

### Post by rubicon on 2008-01-06
Um. What exactly you want to do? Just get Wesnoth on your box?

If so, go to Synaptic, enable Universe repository there and run ```
sudo apt-get update && sudo apt-get install wesnoth
```This will download all packages and dependencies and then install them.

If you already downloaded all wesnoth* packages and don't want apt-get to download it again (I suppose so), then copy all that packages to /var/cache/apt/archives (may require root privileges). Then run those commands above.

---

### Post by rubicon on 2008-01-06
Right, > **Artificial Intelligence said:**
> you can get them via synaptic. (system tab ---> Administration ----> synaptic). 

;)

If you don't have Internet connection, this will be a bit more difficult.

---

### Post by Perfect Storm on 2008-01-06
> **rubicon said:**
> Right, 
;)

If you don't have Internet connection, this will be a bit more difficult.

Aye, then he needs some dependency packages as well.

libsdl-image
libsdl-mixer
libsdl-net
and theirs dependencies

For wesnoth.

---

### Post by kandza on 2008-01-06
the problem is that i don`t have a system tab and i can`t copy that package to the /var/cache/apt/archives

---

