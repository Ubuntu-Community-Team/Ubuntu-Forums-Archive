---
title: "A little more help please"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by America's Reject on 2005-09-12
Ok, I installed Opera with the help of someone and this guide
```
http://ubuntuforums.org/showthread.php?t=40467&page=1&pp=10
```

Now I get this error.
```
I get this error after doing all of this.

Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/mozilla/plugins/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
```

Changing the path does not work...

---

### Post by wvslkr on 2005-09-12
Open Synaptic and install libmotif3 or in terminal type >sudo apt-get install libmotif3.  

Make sure all of the repositories are enabled in your apt sources, I believe this is in multiverse.

---

### Post by America's Reject on 2005-09-12
[QUOTE=wvslkr]Open Synaptic and install libmotif3 or in terminal type >sudo apt-get install libmotif3.  

Make sure all of the repositories are enabled in your apt sources, I believe this is in multiverse.[/QUOTE]
 Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmotif3.

---

### Post by wvslkr on 2005-09-12
Go to this link  [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and follow the instructions to enable extra repositories, then install.

---

### Post by America's Reject on 2005-09-12
[QUOTE=wvslkr]Go to this link  [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and follow the instructions to enable extra repositories, then install.[/QUOTE]
 [http://ubuntuforums.org/showpost.php?p=347550&postcount=13](http://ubuntuforums.org/showpost.php?p=347550&postcount=13)

---

