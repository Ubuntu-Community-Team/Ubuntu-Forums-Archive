---
title: "File System Organizing"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by sparticus06 on 2007-04-27
So, I recently switched to Ubuntu from Win Xp, I am totally loving it too. 

In Xp, many times random/crap files would end up all over the place (in the root of C:) usually when you uninstall a program and it leaves its traces everywhere and it would really take up unnecessary space and make everything look unorganized.

Anyways, does this happen with Ubuntu? Do I need to go through the file systems after a few months and clear unwanted crap out?

Also...Im using Gnome, if I install Amorak via Synaptic, will it mess things up?

Thanks!!

---

### Post by Cypher on 2007-04-27
With Ubuntu you will not have random files strewn across your filesystem in locations you can't find. For any package is installed, you can do "dpkg -L <PKG-NAME>" and it will list all the files that are comprised in that package. If you remove that package, ALL files are removed with no trace left.

You should be able to install Amorak and it will bring in the necessary KDE Libs to function, but should work no problem..

---

### Post by sparticus06 on 2007-04-27
Awesome, that is amazing. 

I seriously am loving my Ubuntu.

---

### Post by jfinkels on 2007-04-27
> **sparticus06 said:**
> So, I recently switched to Ubuntu from Win Xp, I am totally loving it too. 

In Xp, many times random/crap files would end up all over the place (in the root of C:) usually when you uninstall a program and it leaves its traces everywhere and it would really take up unnecessary space and make everything look unorganized.

Anyways, does this happen with Ubuntu? Do I need to go through the file systems after a few months and clear unwanted crap out?

Not really. I guess you could clear out a cache or two here or there, but for the most part, you are in control of how things get done on your computer now. And also, the structure of the filesystem is highly standardized, so all binaries go in /usr/bin/, config files go in /etc, temp files go in /tmp, etc.
> 
Also...Im using Gnome, if I install Amorak via Synaptic, will it mess things up?

Nope, but it'll look a little out of sync with the graphical style of the rest of the GNOME desktop. Amarok is an application designed for KDE, so it, along with most other KDE applications, uses the "Qt" graphical toolkit. GNOME applications use the "Gtk+" toolkit, so they will all look similar.

There are several music management applications that will look good with GNOME. You may want to take a look at Exaile, which is Amarok-like. Also try Banshee, Quod Libet, Rhythmbox, Listen!, etc.

---

### Post by Cypher on 2007-04-27
And Ubuntu loves you too..in that non-human, Linux is superior way..;)

---

### Post by crav on 2007-04-27
Sparticus, perhaps a bit of a preemptive strike, but I had problems playing mp3s when I first got Amarok. Here's the link that got me all sorted out:
[http://ubuntuforums.org/showthread.php?t=421527](http://ubuntuforums.org/showthread.php?t=421527)

---

