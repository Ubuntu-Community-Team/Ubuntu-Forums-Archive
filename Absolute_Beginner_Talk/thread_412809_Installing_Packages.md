---
title: "Installing Packages"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by p3_Arme on 2007-04-18
I have downloaded and am trying to install Edgy Debian Packages, Most of them have installed no problem, however in the Depencies list one of the items it requires is the program itself, I am unable to install them as they get half way through and then crash, although everything else works. 

The packages are: libqt4-gui, and libqt4-qt3support. 

I am installing gnudoq, for my Sudoku puzzles, and it requires these two packages :)
Any help would be grateful.

---

### Post by aysiu on 2007-04-18
Is there some reason you can't use the package manager?

Do you not have an internet connection on your Xubuntu computer?

---

### Post by p3_Arme on 2007-04-18
No I don't, currently I have access to the Interweb on my boyfriends laptop and PC which runs XP :) So I download my programs onto a flash drive, or a CD then transfer them to my laptop, my laptop is old, Ancient in fact so it doesn't know what the internet is, or what a network card is either ;)

---

### Post by az on 2007-04-18
> **p3_Arme said:**
> I have downloaded and am trying to install Edgy Debian Packages, Most of them have installed no problem, however in the Depencies list one of the items it requires is the program itself, I am unable to install them as they get half way through and then crash, although everything else works. 

The packages are: libqt4-gui, and libqt4-qt3support. 

I am installing gnudoq, for my Sudoku puzzles, and it requires these two packages :)
Any help would be grateful.

You mean Etch or Edgy?

Ubuntu is not binary-compatible with any other distro or even another release of Ubuntu.  You cannot use packages from Debian on Ubuntu.

I suggest you remove the packages.  You can try to use Ubuntu equivalents, and you can compile them from the deb-src packages to make them run on your system.

---

### Post by zvacet on 2007-04-18
Download it from this site

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

but download their dependencies too.install dependencies first.

---

### Post by p3_Arme on 2007-04-19
I did download from there, the packages are Edgy, I'm running Xubuntu 6.10, so any suggestions or alternatives would be grateful.

Thanks for helping

---

### Post by scanez on 2007-04-19
Which package depends on itself? Under Feisty I see that libqt4-qt3support depends on libqt4-gui, but neither depends on itself. If similar in Edgy, try installing libqt4-gui first and then (separately) install libqt4-qt3support.

---

### Post by p3_Arme on 2007-04-19
Tried that But as the program itself is included in the depencies list. It seems unwilling to install as in it wont. it asks for my password then stalls, or crashes out, although everything else works, the packages just freeze. 

Thanks for the suggestion.

---

