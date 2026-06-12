---
title: "Ubuntu as VMWare machine"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Jeroen27 on 2007-05-08
I don't know who to thank, but Ubuntu :lolflag: **rules**:lolflag:  

I installed the Feisty Fawn version last week monday as a VMWare machine, and started installing and removing apps, and tweaking the system just the way I want it to be.

and here comes the problem, I really would like to make an image of my Ubuntu version, and then restore it as the main OS for my sytem. 

Does anyone have an Idea on how to do this, if it was a MS distribution, than I could use Symantec Ghost, is there an open source alternative for Symantec Ghost for Linux/Ubuntu.

Thanks

Jeroen

---

### Post by Jonne on 2007-05-08
I guess you could just copy over your home directory after installing. As for getting a list of all installed packages: I'm not sure how you could do that, but it should be possible.

If you did any changes to system files, you'll need to back those up too (/etc/apt/sources.list , /etc/fstab).

edit: [here are instructions](http://www.arsgeek.com/?p=564) for getting a list of your packages

---

### Post by zvacet on 2007-05-08
You have AptonCD in your repos.Install it and with it you can copy everything in your var/cache/apt/archives

here is page to get more information 

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

