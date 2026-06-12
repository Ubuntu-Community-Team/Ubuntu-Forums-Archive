---
title: "Help out a newbie"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by andsteele on 2007-11-11
Okay, just installed Ubuntu on my laptop and I'm very happy with it. I'd just like to know a few things:

How do you use Beryl and emerald themes
How to you make shortcuts to windows programs installed in wine
anyway to install ms office 2003 and photoshop cs2?

Thanks in advance
Newbie

---

### Post by Pumalite on 2007-11-11
[http://ubuntusoftware.info/beryl.html](http://ubuntusoftware.info/beryl.html)
[https://help.ubuntu.com/community/CompositeManager/InstallingBeryl](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl)

---

### Post by por100pre1 on 2007-11-11
Which Ubuntu version are you using? Ubuntu 7.04 can use Beryl, Ubuntu 7.10 uses Compiz-Fusion by default.

---

### Post by oilchangeguy on 2007-11-11
> **andsteele said:**
> Okay, just installed Ubuntu on my laptop and I'm very happy with it. I'd just like to know a few things:

How do you use Beryl and emerald themes
How to you make shortcuts to windows programs installed in wine
anyway to install ms office 2003 and photoshop cs2?

Thanks in advance
Newbie

i don't think you can run office, or photoshop in beryl. you'll probably need crossover office. it's a non-free program that can be found at [www.codeweavers.com](www.codeweavers.com)

---

### Post by andsteele on 2007-11-11
I'm using 7.04.

---

### Post by Ub1476 on 2007-11-11
Photoshop CS2 works under Wine. I don't know if MS Oficce 03 does, but I think OpenOffice should be better than it anyway(not better than 07 though:(), it also support .doc by default, and .docx if you take a look at the Google. If you want the windows apps to show at the Desktop, just select them to place an icon on the Desktop when you insall (or you<can navigate to their install folder (/home/username/.wine/drive_c/programfiler/) and copy/paste on Desktop.

Beryl is now called Compiz-Fusion. Compiz-Fusion is installed by default on the latest Ubuntu (Gutsy Gibbon 7.10). You might have to go into System>Administration>Restricted Driver Manager and and enable/install your graphic card driver to get 3d working. After that just go into System>Preferences>Appearance>Visual Effects and enale it. If you want custom, you need to download the compiz configurato. You can search for it in Synaptic (System>Admin>Synaptic) and download and install it. 

Hope that helps:)

---

### Post by Tyke91 on 2007-11-11
to get beryl in 7.04 type this into a terminal

```
sudo apt-get install beryl beryl-manager emerald-themes
```OpenOffice 2.3 should be more than enough to replace MSOffice 2003

gimp is good for most photoshop things, although you can also get GIMPshop if you want to have that photoshop feel.

beryl has stopped being developed and has merged into compiz to form compiz-fusion. beryl on it's own is ok, but it is a bit unstable. 

edit: Ub1476 is assuming you are on 7.10   it is probably a good idea to switch over to it in the next few months, but if you don't want to you can just use normal beryl from the repositories. 

OR

you can go into the synaptic package manager, do a search on compiz and install the components you need (I've never actually installed compiz-fusion before, so i don't know the exact terminal command..

---

### Post by andsteele on 2007-11-11
Okay I installed beryl manager but every time I try and open it I get a blank white screen. I think it has something to with my graphics card since it's an on bored card by Intel with 64mb of ram. Is there any way to use an emerald theme without having to have a giant 3d cube?

---

### Post by mikecomua on 2007-11-11
Yes just go to the settings.

---

