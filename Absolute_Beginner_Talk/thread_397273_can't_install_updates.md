---
title: "can't install updates"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by PLIACHAS PASCHALIS on 2007-03-30
i see the icon that informs me that there are updates available. i click on the icon and the window opens. i click on the install updates button. I see a msgbox, another one that is checking the available updates but the updates are still there (not installed)
the updates  are kdelibs-data and kdelibs4c2a.
what is happening?

---

### Post by yabbadabbadont on 2007-03-30
Just as a test, close the update window.  Open a terminal window.  Run the following:
```
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by lamalex on 2007-03-30
maybe try running it from terminal, maybe it will give you some useful information to debug

---

### Post by PLIACHAS PASCHALIS on 2007-03-30
I GET THE FOLLOWING: 
dpkg: syntax error: unknown user `backuppc' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
pc04new@pc04new:~$ 


IS THIS TELLING YOU SOMETHING?
thanks for help

---

### Post by xdarkxanarchyx on 2007-05-29
I am having a similar problem.
```

dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

---

### Post by slasko on 2008-04-21
[COLOR="DimGray"]server@server:/etc$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  gs-esp gs-esp-x libgs-esp8 libpoppler1 libpoppler1-glib poppler-utils rsync
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4226kB of archives.
After unpacking 32,8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: syntax error: unknown user `backuppc' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
server@server:/etc$[/COLOR]

I have the same problem, can´t upgrade?

---

### Post by slasko on 2008-04-21
Got it working wiith *dpkg --purge --force-all package_name*

[http://www.linuxquestions.org/questions/debian-26/broken-package-during-upgrade-unable-to-fix-488534/]("http://www.linuxquestions.org/questions/debian-26/broken-package-during-upgrade-unable-to-fix-488534/")

---

