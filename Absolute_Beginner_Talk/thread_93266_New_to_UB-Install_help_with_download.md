---
title: "New to UB-Install help with download"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by lperyer on 2005-11-21
:confused: Ok, I downloaded Minicom for work. File is Downloaded in /home/lonny (thats me-chuckle) The file nam is Minicom-2.00.src.tar.gz, duh what? I know there are different ways to do this. Terminal or another application, like archive manager (I think). Help would be appreciated. were do I go from here?

---

### Post by canadianwriterman on 2005-11-21
You'll need to upzip the tarball first. Double click on it in Nautilus, then extract it. You'll then have the files for installation... maybe a .deb file. If you have a .deb after unzipping, use the terminal:

sudo dpkg install [name of file .deb]

---

### Post by Brunellus on 2005-11-21
is minicom not in the repositories?

enable your additional repositories according to these directions

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Refresh, and search for minicom via synaptic.

---

