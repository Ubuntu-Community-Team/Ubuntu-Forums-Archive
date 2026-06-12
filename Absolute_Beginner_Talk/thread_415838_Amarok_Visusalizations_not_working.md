---
title: "Amarok Visusalizations not working"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by stevehc on 2007-04-20
Hi,

Totally new to Linux and Ubunta.  Finally managed to get the ATI graphics card working with 1280x1024...

Anyway, this Amarok seems quite good.  Cant get the visualisations to work, and cant seem to find why.
Using Feisty (installed it yesterday).

message from Amarok:
No Visualizations Found
Possible reasons:
libvisual is not installed
No libvisual plugins are installed
Please check these possibilities and restart Amarok.

How to fix?
Also, Amarok seems to slowdown a lot with large collections ~> 25000 - any hints?

Many thanks.

---

### Post by ewankho on 2007-04-21
Had the same problem before. I think libvisual is installed by default but the libvisual plugins are not. You need to install both.

---

### Post by stevehc on 2007-04-21
ewankho - thanks.

sudo apt-get install libvisual-0.4-0 libvisual-0.4-plugins

fixed it.

I thinks Amarok seriously rocks!!!

This Ubuntu thing is very cool

---

### Post by sinewalker on 2007-07-26
Another minor tip:

If for some reason the above install of l[FONT="Fixedsys"]ibvisual-0.4-plugins[/FONT] doesn't work for you (because apt can't find the package), try switching to the main repository instead of your local one.  e.g. in Australia, the Multiverse/Universe repositories are sometimes behind, and I couldn't install.  I used Adept Manager to change to the main server, then installed the libvisual plugins from adept.

Don't forget to change back to your local server after this work-around... ;-)

---

