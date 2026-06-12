---
title: "Does anyone know what this prog is?"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by ps2swap on 2005-11-19
Hello,

I am new at ubuntu, so please be gentle!  I have uploaded a pic from a desktop using ubuntu.  I am trying to workout the program being used.  It monitors the system and has a weather plugin.  Does anyone know what it is?

If I have posted in the wrong forum, my apologies!

Thanks!

---

### Post by matthew on 2005-11-19
Those are gDesklets. You can install the program using Synaptic.

First: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Then install using synaptic or by typing this in a terminal
```
sudo apt-get update
sudo apt-get install gdesklets
```

To get different "desklets" (what that means will be clear momentarily) go to the main page and download the ones you want.

[http://gdesklets.gnomedesktop.org/index.php](http://gdesklets.gnomedesktop.org/index.php)

To install them, download the desklet you want to your home directory or desktop. Run the gdesklets program. Drag the desklet file into the gdesklets window and it will install. Click on it in gdesklets and move your cursor onto your desktop to place a desklet where you want it.

That's pretty much it.

To make it run automatically at startup:
System->Preferences->Sessions
Click the Startup tab
Click add and enter gdesklets

---

### Post by ps2swap on 2005-11-19
Thanks a bunch matthew!

Helped heaps!

---

### Post by estel on 2005-11-19
The majority of the working desklets are included in the required gdesklets-data package.

---

