---
title: "I just downloaded supertux , How do i install it..?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-09-26
supertux-0.1.2.x86.package

It's an **.sh** thing...How do you ( i ) install an .sh    ..?

```
sudo apt-get install supertux
``` Dosen't work..

> jason@Hp-Vectra-VL:~$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: You may want to run apt-get update to correct these problems
E: Couldn't find package supertux
jason@Hp-Vectra-VL:~$


> You may want to run apt-get update to correct these problems

I just did an hour or so ago..](*,)

---

### Post by deadgobby on 2006-09-26
For one you are using breezy, but the program should of been in Synaptic. First fix the broken pack and try to reinstall. 
Gobby

---

### Post by JAwuku on 2006-09-26
This is not on the apt-get repository, but is an Autopackage.

Autopackages are a neat way to automatically install applications and games regardless of what Linux distro you are using.

All you have to do is to run the command to install it.

First, make the package executable ```
chmod +x supertux-0.1.2.x86.package
```

then to run it:

```
./supertux-0.1.2.x86.package
```

Some messages come up on the screen, and it may have to download the Autopackage code before continuing.

You can get instructions to install an autopackage at [http://www.autopackage.org/docs/howto-install/](http://www.autopackage.org/docs/howto-install/) , where it shows the GUI way to do what I put above.

Hope this helps! :)

---

