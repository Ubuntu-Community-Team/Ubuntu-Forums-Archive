---
title: "When downloading programs from internet?"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by lperyer on 2005-11-22
I want to download a program from tucows. Is there a certain place it should be saved? Is there a certain program in Ubutunu that I should use to install it? The program is DOSEMU.. Will it install into the menu? :rolleyes:

---

### Post by odin on 2005-11-22
In order to help you i need to know what kind of file what you wanna download is.About downloading into a specific directory I would say that It doesnt matter.

I suggest you to try synaptic or apt to download and install a program before getting it from any web.

---

### Post by aysiu on 2005-11-22
I have a better idea.
Follow the directions in my sig to get more repositories.
Then open up a terminal and type this in ```
sudo apt-get update
sudo apt-get install dosemu
``` That command will download and install DOSEMU and all its dependencies.

---

### Post by Brunellus on 2005-11-22
dosemu is in the universe repositories, I think.  Follow the directions for adding extra repositories here:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

and search for dosemu in Synaptic (System>Administration>Synaptic Package Manager)

---

### Post by lperyer on 2005-11-22
It is a .tgz file. I looked on synaptic, it didnt have it listed. So I was gonna download it from DOSEMU.org

---

### Post by cstudent on 2005-11-22
You can search Synaptic for Dosemu, but I don't recall it being there. Their website is [http://www.dosemu.org/](http://www.dosemu.org/) and they'll point you to Souceforge.net to download. Sourceforge may have some documentation to help you.

Bill

---

### Post by Brunellus on 2005-11-22
if it's a source tarball, you will need the build-essential package to compile it and install it. 

sudo apt-get install build-essential

---

### Post by aysiu on 2005-11-22
[QUOTE=lperyer]It is a .tgz file. I looked on synaptic, it didnt have it listed. So I was gonna download it from DOSEMU.org[/QUOTE] It didn't have it listed because you have to enable extra repositories. To enable extra repositories, follow the instructions in the first link in my signature.

---

### Post by Delkster on 2005-11-22
[QUOTE=lperyer]I looked on synaptic, it didnt have it listed.[/QUOTE]
It seems to be in the multiverse (non-free software) repository, so if you want to get it via Synaptic, you'll need to enable that repository first. I think someone else already posted a link to instructions for doing that.

You may also want to check out DOSbox which is in the universe repository. I haven't used dosemu myself but have used DOSbox. It may take some tweaking to get it working the way you want but it shouldn't be too hard and at least installing it should be easy. I'm not sure if it installs a menu item for you but you can start it with the `dosbox' command. Additional information on configuring it can (probably) be found in the /usr/share/doc/dosbox folder.

---

