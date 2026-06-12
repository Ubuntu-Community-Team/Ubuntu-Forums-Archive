---
title: "ubuntu-desktop"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2005-12-20
hi, 
anyone knows how easy or how hard is to uninstall the ubuntu-desktop, xubuntu-desktop and kubuntu-desktop?

i've installed an ubuntu server without a desktop manager and i want to put any but i want to know how hard is to uninstall it (just in case)

thanks

---

### Post by bscbrit on 2005-12-20
It is as easy as installing them in the first place.  Using synaptic you can mark an uninstalled package for installation, or mark an installed package for removal.  The rest is automagic! 

EDIT Without a desktop manager you will not be running synaptic - but apt-get has the same capabilities.

:p (Actually, that is not true - the system relies on little Ubuntu pixies to do the work but we are trying to keep it a secret)

---

### Post by Knomefan on 2005-12-20
Actually, it's a little problematic, as ubuntu-desktop are just meta-packages, that install other packages and if you uninstall the meta-package the other packages will stay on your system. 

But do not despair, help is nigh:
[http://ubuntuforums.org/showthread.php?t=96046](http://ubuntuforums.org/showthread.php?t=96046)
[http://ubuntuforums.org/showthread.php?t=96048](http://ubuntuforums.org/showthread.php?t=96048)

---

### Post by aysiu on 2005-12-20
I wrote the HowTos Knomefan pointed to. The safest way to do this, though, is to ```
sudo apt-get install
``` whatever you want to install but before saying "yes," highlighting all the packages marked for installation and saving that list in a text file.

Later on, if you want things back the way they were, you can ```
sudo apt-get remove
``` and paste in the packages from the text file.

---

### Post by Adrian on 2005-12-20
[QUOTE=lreyes6]hi, 
anyone knows how easy or how hard is to uninstall the ubuntu-desktop, xubuntu-desktop and kubuntu-desktop?

i've installed an ubuntu server without a desktop manager and i want to put any but i want to know how hard is to uninstall it (just in case)

thanks[/QUOTE]

They are very easy to install! However, since they are meta-packages, uninstalling them is more difficult. Check out these threads for more info:
[http://www.ubuntuforums.org/showthread.php?t=96046](http://www.ubuntuforums.org/showthread.php?t=96046)
[http://www.ubuntuforums.org/showthread.php?t=96048](http://www.ubuntuforums.org/showthread.php?t=96048)

Edit: Respect to Knomefan for being much faster :)

---

### Post by bscbrit on 2005-12-20
Knomefan, yes you are correct, but it depends if the user is actually trying to remove the packages to recover the disk space, or whether he/she simply wants to automatically switch to the command line after having used a GUI.
I assumed the latter but I could be wrong.

---

### Post by lcg on 2005-12-20
[QUOTE=lreyes6]anyone knows how easy or how hard is to uninstall the ubuntu-desktop, xubuntu-desktop and kubuntu-desktop?[/QUOTE]
Removing the package itself is not hard. However, removing the packages which are installed along as dependencies is.

I suggest you install (k|x)?ubuntu-desktop using aptitude. Aptitude marks packages, which are pulled in by other packages as dependencies, as automatically installed. As soon as you remove all packages depending on them, "auto" packages are removed as well.

Note that this only works if you use aptitude for installation and removal. If you have already installed one of these packages without aptitude's help, you can try debfoster after removing it, although I have never used it myself.

HTH,
Lars

---

### Post by lreyes6 on 2005-12-20
thanks everyone... the idea of marking all the packages so i only copy paste the list, if i need to unistall them looks the fastest one but that lead me to another question.... how do i select text in the server mode (no graphical interface) or how to  enable the mouse on the server mode... i think im gonna open another thread for this je

---

