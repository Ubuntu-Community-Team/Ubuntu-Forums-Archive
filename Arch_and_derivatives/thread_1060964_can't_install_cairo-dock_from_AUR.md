---
title: "can't install cairo-dock from AUR"
date: 2009-02-05
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-05
i downloaded two packages(tar.gz)(one is cairo-dock and the other is cairo-dock plugins) from 
[http://aur.archlinux.org/packages.php?ID=15201](http://aur.archlinux.org/packages.php?ID=15201) and
[http://aur.archlinux.org/packages.php?ID=15202](http://aur.archlinux.org/packages.php?ID=15202)

i copied them over to a directory in my home folder called builds_AUR,and extracted them.then i opened up a terminal and did the following to install,but failed to do so:

[sonujha@arch ~]$ cd builds_AUR
[sonujha@arch builds_AUR]$ makepkg
==> ERROR: PKGBUILD does not exist.
[sonujha@arch builds_AUR]$ 


i have already installed the necessary tools by:

$sudo pacman -Sy base-devplease tell me if i am missing something.How do i proceed with the installation?

---

### Post by smartboyathome on 2009-02-05
You need to extract the tar.gz to your current folder, then edit the PKGBUILD to your liking, then build it with makepkg.

---

### Post by stonecoldjha on 2009-02-05
how is that done?:)

---

### Post by stonecoldjha on 2009-02-05
ok,i got that.but,now again it did not succeed as you can see:


[sonujha@arch ~]$ cd Desktop
[sonujha@arch Desktop]$ makepkg
==> ERROR: PKGBUILD does not exist.
[sonujha@arch Desktop]$ cd cairo-dock
[sonujha@arch cairo-dock]$ makepkg
==> Making package: cairo-dock 1.6.3.1-2 i686 (Thu Feb  5 22:39:08 IST 2009)
==> Checking Runtime Dependencies...
==> Missing Dependencies:
  -> cairo-wglitz
==> Checking Buildtime Dependencies...
==> Missing Dependencies:
  -> intltool
==> ERROR: Could not resolve all dependencies.
[sonujha@arch cairo-dock]$

---

### Post by smartboyathome on 2009-02-05
Why don't you just use yaourt? It does it for you automatically. See the Wiki for more info.

---

### Post by gjoellee on 2009-02-05
> **smartboyathome said:**
> Why don't you just use yaourt? It does it for you automatically. See the Wiki for more info.
+1 for yaourt

---

### Post by stonecoldjha on 2009-02-05
i installed cairo-dock and plugins using yaourt,but how do i launch it.its not there in applications>preferences
n ubuntu i have it in applications>sytem tools>cairo-dock.also,in ubuntu,i can launch it by the command "cairo-dock".but,even after installing from the AUR using yaourt i can neither launch it,nor can i find it in applications>system tools or anywhere in the menu.how do i see if it got properly installed?aren't there other ways of installing it?

---

### Post by stonecoldjha on 2009-02-05
i just did the following,and learnt that cairo-dock is not there:

[sonujha@arch ~]$ sudo pacman -Si cairo-dock
error: package 'cairo-dock' was not found
[sonujha@arch ~]$


what do i do now?how do i install it?please help me install it because i need it and like it so much.

---

### Post by &#32 Greg on 2009-02-05
Did you install cairo-wglitz before cairo-dock?

pacman -Rd cairo
yaourt -S compiz-wglitz

---

### Post by RiceMonster on 2009-02-05
> **stonecoldjha said:**
> ok,i got that.but,now again it did not succeed as you can see:


[sonujha@arch ~]$ cd Desktop
[sonujha@arch Desktop]$ makepkg
==> ERROR: PKGBUILD does not exist.
[sonujha@arch Desktop]$ cd cairo-dock
[sonujha@arch cairo-dock]$ makepkg
==> Making package: cairo-dock 1.6.3.1-2 i686 (Thu Feb  5 22:39:08 IST 2009)
==> Checking Runtime Dependencies...
==> Missing Dependencies:
  -> cairo-wglitz
==> Checking Buildtime Dependencies...
==> Missing Dependencies:
  -> intltool
==> ERROR: Could not resolve all dependencies.
[sonujha@arch cairo-dock]$

type

```
makepkg -cs
```
That pulls in the dependencies and builds the package.

or just use yoaurt, as reccomended. That's even easier.

> **stonecoldjha said:**
> i just did the following,and learnt that cairo-dock is not there:

[sonujha@arch ~]$ sudo pacman -Si cairo-dock
error: package 'cairo-dock' was not found
[sonujha@arch ~]$


what do i do now?how do i install it?please help me install it because i need it and like it so much.

-Si searches for and displays information about a specif package in the repos (cairo-dock.pkg.tar.gz in this case). Since you're installing it from the AUR, it won't be there.

Try this (doesn't need to be as root):
```
pacman -Qi cairo-dock
```

That will search your local package database. If you want to do a more open ended search (keywords) use -Ss for the repos and -Qs for your local database.

---

### Post by stonecoldjha on 2009-02-06
the following is the output:

[sonujha@arch ~]$ pacman -Qi cairo-dock
error: package "cairo-dock" not found
[sonujha@arch ~]$

---

### Post by stonecoldjha on 2009-02-06
i have tried installing cairo-dock several times using
#yaourt -S cairo-dock
saying yes to all the questions that i am asked while installation.
when it seems to be completed,i run
$cairo-dock
but the i get the output  "command not found" .

please tell me what should i do?

---

### Post by stonecoldjha on 2009-02-06
i somehow managed to install cairo-dock and plugins,but i removed all icons from the dock,and was left with a blank dock,and i was unable to add new icons to it.so,i decided to tremove cairo-dock and then reinstall it.but,after reinstalling,when i launched cairo-dock i saw the same theme and the same blank dock that i was using last time.
now,please tell me the way to completely obliterate cairo-dock,purging,everything,be it config files,etc. so that when i reinstall it,it behaves as if it is being installed for the very first time,and doesn't take settings that i made in the last install.

---

### Post by Rumor on 2009-02-06
stonecoldjha: You *really* need to spend some time digging through the wiki and the forums. The documentation is quite thorough and covers most of the issues you have raised recently.

To your immediate question:

The [wiki page for yaourt]("http://wiki.archlinux.org/index.php/Yaourt") tells you that it is a wrapper for pacman.

Hence, all the commands you would use for [pacman]("http://wiki.archlinux.org/index.php/Pacman") will work with yaourt.

Including those for [removing packages.]("http://wiki.archlinux.org/index.php/Pacman#Removing_Packages")

---

### Post by stonecoldjha on 2009-02-06
i have referred to it,but it doesn't tell as to how i can remove my personal config files in my home directory.and i don't see any of them in my home directory.

---

### Post by Rumor on 2009-02-06
How are you looking for them? When you say you "don't see any." What method are you using to view them? Are you trying to list them in your terminal using ls -la? What dotfiles do you see in your terminal output? Are you trying to view them in a graphical file manager, and if so, which one? Again, what dotfiles does it show you?

Information like that may seem irrelevant, but it helps us understand what steps you are taking so we can help you along the path.

---

