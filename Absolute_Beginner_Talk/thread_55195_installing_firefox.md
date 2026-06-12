---
title: "installing firefox"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by robwowk on 2005-08-07
I searched for this, found nothing, so here goes. I'm pretty new to linux, just got internet up on here because my card wasn't compatible (had to use use ndiswrapper). Now, I've downloading firefox, and for the life of me, I have no idea how to install it. Any help is appreciated.

---

### Post by woedend on 2005-08-07
[QUOTE=robwowk]I searched for this, found nothing, so here goes. I'm pretty new to linux, just got internet up on here because my card wasn't compatible (had to use use ndiswrapper). Now, I've downloading firefox, and for the life of me, I have no idea how to install it. Any help is appreciated.[/QUOTE]
 what makes debian based so great is the package management...use it!  save yourself a headache.  click system->administration->synaptic, search for firefox, put a check in the box next to it, and click apply.

---

### Post by aysiu on 2005-08-07
Installing the downloaded Firefox isn't as "easy" as doing so through Synaptic, but it's also not that difficult, and it can be done all graphically.

If you want to install Mozilla's download, double-click the .tar.gz file.
It will appear to open in a folder.
Click "extract."
Then the extracted folder will have a file called "firefox-installer."
Double-click that file, and it will install.
Then, you'll have a folder (stupidly) named firefox-installer.
Just call that folder whatever you want, and the launcher for the program will be a file inside called "firefox."
You'll have to create your own custom launchers and shortcuts for it, though.

Even though Synaptic's easier, I prefer the Mozilla Firefox over Ubuntu's Firefox for a really silly reason--I like the "real" fox logo, not the blue world *sans* fox.

---

### Post by robwowk on 2005-08-07
i tried that...when I click on firefox-installer, nothing happens.


same thing is happening with opera, too

---

### Post by aysiu on 2005-08-07
Weird. Just use Synaptic Package Manager, then. It's far easier.

---

### Post by robwowk on 2005-08-07
did that and nothing happened. it says no space is added or taken, so I'm assuming its already installed?

---

### Post by aysiu on 2005-08-07
Yeah, in fact, the default Ubuntu install should not only have Firefox already installed, but it should already be an icon on your panel (as I said before, it's an ugly blue circle, not the fox around the world you're probably used to).

You may, however, have an older version (1.0.4, for example).

In Synaptic, click Reload. Then, search for Firefox. Right-click the checkbox and select "mark for upgrade." Then, click Apply. You'll get the latest (1.0.6) version of Firefox, then.

---

### Post by robwowk on 2005-08-09
ah okay...got it...


well anyway


how would i install opera..just for the sake of knowing these things  :)

---

### Post by WirelessMike on 2005-08-09
> **robwowk**:
how would i install opera..just for the sake of knowing these things

Easy...

Download Linux version for Ubuntu (they have it) from Opera.com.

Open a terminal, cd to the directory you downloaded the file.  It's a deb file, so just dpkg -i opera-static_8.02-20050727.1-qt_en_i386.deb (or whatever the filename is when you download it).

That's all there is to it.

Don't know why you'd be interested, though...  It's not open source and if you really like it, you'll have to pay for it to get a full version with no ads.

---

### Post by robwowk on 2005-08-09
ive always been a fan of opera...its just kinda what im used to.

---

