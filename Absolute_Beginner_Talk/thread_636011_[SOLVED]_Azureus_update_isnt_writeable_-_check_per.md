---
title: "[SOLVED] Azureus update isnt writeable - check permission - how do i solve this?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-09
how do i solve this please?

each time i start Azureus, it downloads this and fails to update

see pic attached

---

### Post by jken146 on 2007-12-09
Try running Azureus as sudo, i.e. ```
sudo azureus
```

---

### Post by MozartlovesUbun2 on 2007-12-09
> **jken146 said:**
> Try running Azureus as sudo, i.e. ```
sudo azureus
```

ok, i'll try that, thanks

=================

hmmm, ok i did sudo su first in the terminal and then "azureus" but it seems that didn't help me much

---

### Post by MozartlovesUbun2 on 2007-12-11
Linux/Unix notes

If you installed Azureus 3.0.2.0 or higher, you can also try a manual update.

   1. Make sure Azureus is not running
   2. Open up a shell
   3. Change to the azureus program dir
   4. Run "./updateAzureus" (If this is your first time using the script, you may have to "chmod +x ./updateAzureus"). If you don't have this script, you can create one: 

sudo java -cp ./plugins/azupdater/Updater.jar org.gudy.azureus2.update.Updater updateonly `pwd` ~/.azureus

Assuming you have a ./plugins/azupdater/Updater.jar, this will elevate your rights and apply any updates that couldn't be done with your normal user's rights. 
=================================================

sorry can  someone tell me

**how to change to the  azureus program dir**

**how does one do chmod +x?**

**do i need the ` ` around the password**

is this the right directory? (please see pic)** is it supposed to be in the home directory or system files?**

---

### Post by Perfect Storm on 2007-12-11
It's not sudo azureus but gksudo azureus when messing with gui applications.

You can check this guide, how to change it: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

Though I would recommend any other torrent application than Azureus. (like Deluge).

---

### Post by MozartlovesUbun2 on 2007-12-11
> **Artificial Intelligence said:**
> It's not sudo azureus but gksudo azureus when messing with gui applications.

You can check this guide, how to change it: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

Though I would recommend any other torrent application than Azureus. (like Deluge).

Thanks AI

ok cool i'll check out deluge, (just to know, do you prefer the others over azureus because they are faster or stable? is azureus not open source, i dont know?)

Thanks

---

### Post by philinux on 2007-12-11
Azureus is buggy and a resource hogger. Deluge is pretty damn good.

---

### Post by Perfect Storm on 2007-12-11
Azureus is a resource hog plus it requires java (nothing wrong with java but it takes resources as well) and Azureus is a bit slow and I've seen my share of annoying bugs on it. That's my only grunge against it.

At Deluge homepage you'll find ubuntu packages with the newest version. Easy to install and use.

---

### Post by MozartlovesUbun2 on 2007-12-11
ok thanks, i havnt tried Deluge yet, will do now, guess was using Azureus as i use it in windows too, actually i like uTorrent better, more cleaner, but Azureus never gives me any problems with ports and so, usually in the other torrent apps i have to go to the router and open ports, and java i need anyway as i use sites where java should be installed. the new video interface of azureus seems interesting too, a bit like MIRO, (my miro crashes a lot now, just closes down as soon as i start it)

---

