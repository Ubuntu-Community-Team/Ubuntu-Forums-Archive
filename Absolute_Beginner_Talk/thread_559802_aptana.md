---
title: "aptana"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by gryzzly on 2007-09-25
hi people. 
i'm sorry that i have maybe not enough patience for reading everything i can, but maybe it is more about time, cuz i think solution must be simple.
So i am very new with linux, but i already like it very much, 
and question is:
 I downloaded [aptana IDE]("http://aptana.com")  cuz its nice open source IDE which i btw recomend very much. So i pushed executable after i rearchived the zip i downloaded, and then, somehow i moved everything i installed to the /usr/share/pixmaps/aptana/... - cuz i was trying to make icon for it.
so, my question is - now i have this folder in /usr/share/pixmaps/aptana/,,, where probably everything that this app needs to start and work... So, where i need to move files now? to which address?

Thanks for help, guys.

---

### Post by ofb on 2007-10-03
Disclaimer: I'm still getting the hang of Ubuntu myself.

You're asking, where does one usually put executables? In a /bin. (short for 'binary')

This sort, an application for general users that has nothing to do with the running of the system, it would be /usr/bin.

However, a /bin is usually just for the executables, and the various other parts of an application, like libraries and help docs and icons, go in different directories for their respective file types.

What's Aptana like? From the website I'm wondering if it's one of the Java applications that's more like a Windows app -- everthing goes in one directory. I tend to install those to a subdirectory of my /home, like /home/me/apps. It's simple, and there's no messing around with permissions, and works fine for a single user computer.

This is handy.
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by hyper_ch on 2007-10-03
Had a look at this?

[http://www.howtoforge.com/aptana_ajax_ide_ubuntu](http://www.howtoforge.com/aptana_ajax_ide_ubuntu)

---

