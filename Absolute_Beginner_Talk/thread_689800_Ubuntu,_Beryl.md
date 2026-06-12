---
title: "Ubuntu, Beryl?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-06
Alright, so I have the newest Ubuntu installed, now I know the best upgrade type of thing for Ubuntu is Beryl. Just like Macs, is OS X Leopard. Now I'm new to Linux in general, so could somebody help me get beryl? Thank you.

---

### Post by jordanmthomas on 2008-02-06
I believe you are confused.  Beryl is just a (now obsolete) window manager.  It is not akin to Leopard.  Leopard in your analogy would be analogous to Gutsy itself.

Beryl has been merged into compiz, which is installed by default with Ubuntu.  
```
system --> preferences --> appearances
```
Then, click on the desktop effects tab and you can (probably) enable desktop effects.

---

### Post by emarkd on 2008-02-06
Beryl has merged with Compiz to form Compiz Fuzion.  If youre running Gutsy, you've already got it.  You can go to System > Preferences > Appearance, click on the Visual Effects tab to enable it.  If you want more control over all of its options, open System > Administraction > Synaptic and install compizconfig-settings-manager

---

### Post by libertas on 2008-02-06
you have compiz fusion already on your computer if you have 7.10 but you don't get much visual effects out of it. the reason being that you do not have the library manager that allows you to utilize all of the plugins (cube effects, trail effects, fire, rain, closing etc.) you need the advanced desktop manager to do this, download it from the synaptics package manager

---

### Post by libertas on 2008-02-06
the file to install is compizconfig-settings-manager from the synaptics manager System > Administration>Synaptics Package manager this fulfill all of your eye candy needs:lolflag:

---

### Post by blasteryui on 2008-02-06
When I select the option to use all the effects, it says about updating the graphics driver. Now how do I update my laptops graphic driver? I don't have windows XP at all BTW.

---

### Post by emarkd on 2008-02-06
You don't need XP.  Go to System > Adminstration > Restricted Drivers and see if there's a driver there for your video card.

---

### Post by blasteryui on 2008-02-06
> **emarkd said:**
> You don't need XP.  Go to System > Adminstration > Restricted Drivers and see if there's a driver there for your video card.

On Linux how do I check what my graphics card is?

---

### Post by nikoPSK on 2008-02-06
> **jordanmthomas said:**
> I believe you are confused.  Beryl is just a (now obsolete) window manager.  It is not akin to Leopard.  Leopard in your analogy would be analogous to Gutsy itself.

Beryl has been merged into compiz, which is installed by default with Ubuntu.  
```
system --> preferences --> appearances
```Then, click on the desktop effects tab and you can (probably) enable desktop effects.

some people still do use beryl. But you might want compiz. It comes by default in gutsy. Just goto Appearance and The Desktop Effects tab and choose a setting. If you want to customize more get compizconfig-settings-manager.

---

### Post by jordanmthomas on 2008-02-06
> On Linux how do I check what my graphics card is?

```
sudo lshw -short -class display
``` is an easy way to find out.  It's likely Ubuntu has some nice tool that tells you in its menus somewhere too.

However, the restriced driver manager should tell you if there's a driver that works for your card.

> some people still do use beryl.
I know, but it's still not being maintained, and thus is obsolete.  :lolflag:

---

### Post by enigmaniac23 on 2008-02-06
Yes, you can also check your video card through the menus if you want.  Just check System --> Preferences --> Hardware Information
You should see your video card in there as well.

---

