---
title: "How do I determine what I have installed?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-17
I've gotten my Ubuntu Linux setup the way I like it and thought about documenting its configuration.
Unfortunately, I've installed a lot of stuff and would like to know what I have done.

Is there a way to find out what has been installed?

Carl

---

### Post by starcraft.man on 2007-05-17
Go System > Administration > Synaptic Package Manager.

On the bottom left, click on the Status button, then in the upper left menu you can click installed and see all the applications/packages in your computer :)

You can also of course remove any you know you don't want by just unchecking them and applying changes :)

---

### Post by bodhi.zazen on 2007-05-17
Easy way ? Start synaptic. Synaptic will list all packages, installed or otherwise.

If you want to do it from the CLI (terminal)

```
dpkg –-get-selections | grep -v deinstall > ubuntu-files
```

Now either ```
less ubuntu-files
``` or open the document with gedit.

---

### Post by vtel57 on 2007-05-17
You can check to see what's in your dpkg.log entries.

Graphic method:

```
 $ gedit /var/log/dpkg.log
```

Command line method:

```
 $ vim /var/log/dpkg.log
```

You may have different versions of the dpkg.log on your system. You can check to see what's actually in the /var/log directory by navigating there with Nautilus or using a command line:

```
 $ ls -a /var/log | more
```

---

