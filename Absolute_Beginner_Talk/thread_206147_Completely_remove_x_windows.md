---
title: "Completely remove x windows"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by underdog on 2006-06-29
Hi,
I did a normal server install of 6.06. I then install x windows with something like
apt-get install x-window-essentials or something along those lines. I also have xfce installed. I just want to completely get rid of it (I don't have much space on the HDD). If this is a hastle, I want to at least change the default run level to command prompt. Thanks.

---

### Post by ovimunt on 2006-06-29
Hi,

You can remove any package using

sudo apt-get remove *x-window-essentials* (this needs to be the exact name of the package)

Yet, I'm not sure if this will fix your problem. Better wait for some more advice before you do this.

---

### Post by underdog on 2006-06-29
Yeah, I tried that already but either I can't remember the name of the package (and i've tried googling a lot), or you can't remove it that way. I tried using aptitude to uninstall it as well, but no sucess. Thanks anyways. Any other suggestions?

---

### Post by ovimunt on 2006-06-29
Boot in Recovery mode and give it a go from there. Maybe it will let you remove it.

---

### Post by aysiu on 2006-06-29
Try this: ```
sudo aptitude remove x-window-system-core
```

---

### Post by uzi09 on 2006-06-29
first of all, type:
```
history
```
and see what command u used to install it with. (u could also look at the .bash_history file for this info)
```
less .bash_history
```

if you can't find the info in there, try typing in **sudo aptitude remove x** then press tab twice to let it show you all the different programs you have installed that start with an x. perhaps it'll ring a bell if you see the program name.

---

### Post by houstonbofh on 2006-06-30
These two pages show you remove the desktop packages.  You will still have to remove X, but this is a lot of the hidden stuff.
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)
[http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

---

