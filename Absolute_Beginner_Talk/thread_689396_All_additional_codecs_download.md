---
title: "All additional codecs download?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by smartygoldenfish on 2008-02-06
I need to download that all additional stuff and codecs to play all media files.
I dont have internet connection on my computer. I have access to cybercafe only.
Can anybody give direct link to a file that can be JUST downloaded and then taken to home and installed?
Can i get similar file for Wine plz.

Last question..would wine run my NFSMW? I run it on xpsp2...would it too?

---

### Post by emarkd on 2008-02-06
This is harder than you think because many packages have dependencies that are not installed by default.  You can try digging through [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/) for what you need.  Dependencies for each package are also listed there.

For your media stuff, try installing the ubuntu-restricted-extras package.  It'll be on that page somewhere.  Wine will be there also.  Not sure what NFSMW is....but if it's software you can check out Wine compatibility at [http://appdb.winehq.com](http://appdb.winehq.com)

---

### Post by ahaslam on 2008-02-06
[http://packages.medibuntu.org/pool/non-free/w/w32codecs/](http://packages.medibuntu.org/pool/non-free/w/w32codecs/)
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

^Should get you going ;)

---

### Post by Jadd on 2008-02-06
Here's how to do it:[LIST]
[*]Open Synaptic Package Manager (System->administration)
[*]Mark the packages you would to download later for installation. In your case they are wine and ubuntu-restricted-extras .
[*]Instead of clicking apply, click File->Generate Package Download Script
[*]Save the file someplace.
[*]Launch your favourite text editor (gedit, for ex), and open the saved script.[/LIST]
You've now got a list of the URLs of the requested packages, including dependencies!

---

### Post by erfahren on 2008-02-06
this may interest you

[Howto: NoNetDebs - upgrade Ubuntu without Internet (or with low-bandwidth connection)](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by ubuntu27 on 2008-02-06
> **Jadd said:**
> Here's how to do it:[LIST]
[*]Open Synaptic Package Manager (System->administration)
[*]Mark the packages you would to download later for installation. In your case they are wine and ubuntu-restricted-extras .
[*]Instead of clicking apply, click File->Generate Package Download Script
[*]Save the file someplace.
[*]Launch your favourite text editor (gedit, for ex), and open the saved script.[/LIST]
You've now got a list of the URLs of the requested packages, including dependencies!

SmartFish, follow Jadd's advice. It works :D

---

