---
title: "what to do with beryl tarball"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Zopiac on 2008-04-19
i got beryl, first on the list at [http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php), extracted the file, and am left with a folder....what do i do with its contents(.m4, .in, .files, .am, etc.)

---

### Post by PeterJS on 2008-04-19
What version of ubuntu are you running? If you're running Gutsy (7.10) it has Compiz Fusion installed by default. Compiz Fusion is the fusion of the compiz and beryl projects, work on beryl has stopped and all effort is now being put in to the combined Compiz Fusion. To enable Compiz, you can go to System > Preferences > Appearance Properties > Visual Effects. Setting the effects level to any level beyond None will enable Compiz Fusion. If you really want to tweak out all of the possible settings install compizconfig-settings-manager, which will add a menu entry at System > Preferences > Advanced Desktop Effects settings.

---

### Post by Zopiac on 2008-04-19
i am running 7.1...

so you're saying i already have beryl? then how do i access, say, the spinny-cubey-workplace switcher thingamaroo?

---

### Post by Lolicon on 2008-04-19
Enable desktop effect.

---

### Post by conscious on 2008-04-19
> **Zopiac said:**
> so you're saying i already have beryl? then how do i access, say, the spinny-cubey-workplace switcher thingamaroo?

Enable advanced desktop effects, install compizconfig-settings-manager.

EDIT: Actually, this question has been already answered by PeterJS (read above).

---

### Post by Zopiac on 2008-04-19
ok, but how do i actually ACCESS it???

---

### Post by PeterJS on 2008-04-19
1) Install compizconfig-settings-manage
2) Go to System > Preferences > Advanced Desktop Effects Settings
3) Under General Options > Desktop Size, set Horizontal size to 4
4) Go back to the main page, scroll down and enable the Desktop Cube plugin
(Optional) Enable the rotate Cube plugin

---

### Post by Zopiac on 2008-04-19
> **PeterJS said:**
> 1) Install compizconfig-settings-manage
2) Go to System > Preferences > Advanced Desktop Effects Settings
3) Under General Options > Desktop Size, set Horizontal size to 4
4) Go back to the main page, scroll down and enable the Desktop Cube plugin
(Optional) Enable the rotate Cube plugin

how do i install  the compizconfig-settings-manage exactly? i have the Extra visual effects, but not sure if thats related? i need specifics :(

---

### Post by steveneddy on 2008-04-19
> **Zopiac said:**
> i got beryl, first on the list at [http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php), extracted the file, and am left with a folder....what do i do with its contents(.m4, .in, .files, .am, etc.)

delete it and use Compiz. :D

---

### Post by dje on 2008-04-19
Do this in a terminal (Applications >> Accessories >> Terminal):
```
sudo apt-get install compizconfig-settings-manager
```

hope that helps,
dje

---

### Post by Zopiac on 2008-04-19
ok im pretty sure it works now:

zopiac@zopiac:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-compizconfig
The following NEW packages will be installed:
  compizconfig-settings-manager python-compizconfig
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 547kB of archives.
After unpacking 3506kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe python-compizconfig 0.5.2+git20070912-0ubuntu1 [36.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe compizconfig-settings-manager 0.5.2+git20070912-0ubuntu1 [511kB]
Fetched 547kB in 2s (211kB/s)                         
Selecting previously deselected package python-compizconfig.
(Reading database ... 115946 files and directories currently installed.)
Unpacking python-compizconfig (from .../python-compizconfig_0.5.2+git20070912-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.5.2+git20070912-0ubuntu1_all.deb) ...
Setting up python-compizconfig (0.5.2+git20070912-0ubuntu1) ...
Setting up compizconfig-settings-manager (0.5.2+git20070912-0ubuntu1) ...

zopiac@zopiac:~$ 



Also, the Advanced Desktop Effects Settings thing is there, so yeah :P

---

### Post by Zopiac on 2008-04-19
ACTUALLY, i have figured it out, for the most part, but i still dont know how to get the cube running :( I have enabled Desktop Cube, used its first action key, labeled Unfold, but still nothing happens. Any ideas?

---

### Post by Whiffle on 2008-04-19
You need to enable the "rotate cube" plugin, and then set the keys in that one.  I think by default its ctrl+alt+left/right, but i'm not certain.

---

### Post by Zopiac on 2008-04-20
the only thing NOW is that, unlike in the youtube video, Beryl, my windows are not layered in 3d. any ideas?

---

### Post by PeterJS on 2008-04-20
The 3d windows plugin was never stabilized and released for Gutsy, but will be making it's return in Hardy. When you update in a couple days you'll get the 3d windows plugin.

---

