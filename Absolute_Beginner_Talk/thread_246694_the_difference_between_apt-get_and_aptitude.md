---
title: "the difference between apt-get and aptitude"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-08-29
what is the difference between apt-get and aptitude? I know both are used to install applications but I dont know what the difference is. There is one answer about this question in the forum but I just want to make sure it is accurate.

Thanks alot.

---

### Post by Toxicity999 on 2006-08-29
Aptitude is an advances console package manager, the console based solution to synaptic if you care to call it that. It also supports fast call like sudo aptitude install xyz or you can launch the package application with sudo aptitude. Aptitude handles packages more inteligently and presents you with solutions to resolve dependancies giving you a score of how it should work out. Apt-get is the most default of apt tools and is powerful for doing what it needs to do but Aptitude is just better in most cases... and it has mine sweeper! Not to mention an easy way to clean obsolete files and cached packages.

---

### Post by bulldog on 2006-08-29
Well if I'm informed correctly,apt-get installs the same way as aptitude.

The difference is with un-installing.
When installed with aptitude,it will un-install all the dependancy's which came with the install.
Apt-get will only un-install the program and let the dependancy's on your hdd.

---

### Post by taurus on 2006-08-29
Aptitude can keep track of what you have installed on your machine better than apt-get, especially if you want to install KDE (kubuntu-desktop) or XFce4 (xubuntu-desktop)...  It makes remove either one of them easier at a later time.

---

### Post by Bachstelze on 2006-08-29
Aptitude remembers dependencies. *Id est*, if you install what is called a "metapackage", like kubuntu-desktop, with apt-get and you want to remove it later, it will remove only the package and not all the ones that depend on it and were installed with it, so tou'll have to remove all of them manually. OTOH, if you install it with aptitude and then you want to remove it, it will also remove all the dependencies.

---

### Post by pbaehr on 2006-08-29
I've also experienced situations where "apt-get upgrade" would mark updates as "held back" and "aptitude upgrade" was able to install the updates without issue.

---

### Post by Toxicity999 on 2006-08-29
Need I again mention the minesweeper? You all know you love it! Haha. Yes Aptitude is more powerful than apt-get as it adds advanced tools to the comandline instead of relying on thing like synaptic. aptitude doesn't really get enough credit as most casual users wont notice any difference. But to the poweruser, it's a real time saver.

---

### Post by Jagot on 2006-08-29
[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

---

