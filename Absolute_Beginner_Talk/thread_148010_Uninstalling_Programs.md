---
title: "Uninstalling Programs"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by YuHoo on 2006-03-21
First off, I am a novice in the linux world. I have used windows since my first computer and only experimented with linux, but failing each time since I simply did not have the time to devote to it. Now with Ubuntu on my laptop I wish I had done this much earlier. I thought I was spoiled with the straight forwardness of win2k. But now for my question.

I am wondering if there is any procedure that is expected when uninstalling programs in Ubuntu. As with windows there are multiple ways to uninstall, but only a few ways that cleans up the system. Is there a similar situation with Ubuntu?

Along with this. Are there any recommended procedures or systems to install programs?

---

### Post by mostwanted on 2006-03-21
[QUOTE=YuHoo]First off, I am a novice in the linux world. I have used windows since my first computer and only experimented with linux, but failing each time since I simply did not have the time to devote to it. Now with Ubuntu on my laptop I wish I had done this much earlier. I thought I was spoiled with the straight forwardness of win2k. But now for my question.

I am wondering if there is any procedure that is expected when uninstalling programs in Ubuntu. As with windows there are multiple ways to uninstall, but only a few ways that cleans up the system. Is there a similar situation with Ubuntu?

Along with this. Are there any recommended procedures or systems to install programs?[/QUOTE]

If you install apps using apt-get or synaptic run
> 
sudo apt-get remove name_of_my_app

or right click on it in Synaptic and select remove/uninstall/whatever the option is called ;)

I believe the adding --purge option will clean most things up:

```
sudo apt-get remove --purge appname
```

If you want to remove programs installed from source there's usually an uninstall built into the makefile, so you navigate to the directory where you untar'ed your package and run

```
sudo make uninstall
```

---

### Post by Ubuntuud on 2006-03-21
Files you installed with a file ending with .package can be uninstalled with a program called (I think) package manager, it's somewhere in the menu...

---

### Post by CompShrink on 2006-03-21
You really should install/uninstall packages with apt-get (when using command line, like an MS-DOS window) or Synaptic. Both use the same database, and they use the officially supported programs from Ubuntu by default.

You can also enable extra unsupported but touched-up-for-Ubuntu packages in Universe and Multiverse sections. 

To do this, click on System (on the top "taskbar") > Administration > Synaptic Package Manager. Then click on Settings > Repositories. Then in the window that pops up, click on the Settings button. The top check box should be "Show disabled software sources" make sure that is checked, then click close. There's still the "Repositories" window open. Check the ones that say Universe and Multiverse, and you can leave the rest alone. Click Ok.

Now click reload and you have all the official supported and unsupported programs that the makers of Ubuntu have made available. You can add more repositories later, or to add indivial *.deb files you downloaded, use:

sudo dpkg -i /path/to/file.deb

Whenever possible use this method to install programs.


Then, when uninstalling, simply open Synaptic, search for what you want to remove, right click on it and choose "remove completely."


It may sound complicated at first, but it's much faster in general, as it's a one stop shop for the vast majority of what you'll want/need to install/uninstall. If you don't know the name of the program you want, you can search by "name and description" while searching for the name of a similar program for windows or mac osx, or a word or two description of what it does.

---

### Post by NESFreak on 2006-03-22
i think he has the same problem as i.
i recently installed wolfenstein:et, but because i'm dualbooting, i'm now running out of space.
I need a clean way (some sort of easy to use uninstallscript or something) to do this.

---

