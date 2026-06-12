---
title: "[SOLVED] Woot, I got XGL working, but how do I use it?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-24
What keys do I press etc.:popcorn:

---

### Post by jan quark on 2007-12-24
If you are using Compiz in Gnome environment download Advanced Desktop Effects Settings with the Add/Remov Assistant. You can configure many things with it.

---

### Post by adam.tropics on 2007-12-24
In a terminal (or find it in synaptic)

```
sudo apt-get install compiz compizconfig-settings-manager
```then hit <ALT>F2

```
compiz --replace
```Then from your menu, system-->preferences-->CompizConfig settings manager to play with your settings.....this all depends on your really having xgl or aiglx definitely running!

edit: and compiz installed!

---

### Post by Afkpuz on 2007-12-24
Definitely install the compiz effects manager.  Then, goto system>Preferences>Appearance>Visual Effects

Select Custom and then click on "preferences".  Here, you can change all the sweet compiz settings.  To get here again, goto System>Preferences>Advanced Desktop Effects Settings

And by the way, make sure you have installed your restricted graphics driver.  System>Administration>Restricted Drivers Manager 

Enjoy!

---

### Post by hilariousness16 on 2007-12-24
I installed what you told me but how do I use the cube thing?

---

### Post by adam.tropics on 2007-12-24
All sorts of info on the [Compiz wiki]("http://wiki.compiz-fusion.org/"), and in case you need it, they too have a [forum.]("http://forum.compiz-fusion.org/")

---

### Post by Afkpuz on 2007-12-24
Ok, assuming that you've chosen "custom" in System>Prefrences>Appearance>Visual Effects, Heres how to cube it up.  

Open the compiz settings manager
System>Preferences>Advanced Desktop Effects Settings

First, make sure that you have at least 4 workspaces.  Goto the General Options place and then on the Desktop size tab.  Set Horizontal virtual size to 4. 

Click the back button, then uncheck "desktop wall" and "desktop plane" if they are checked.  Then, check "Desktop Cube" and "Rotate Cube"

Once done, your cube is enabled with default settings.  You should be able to hold Crtl+Alt and left click to rotate your cube.  However, you probably want to change the default key binding.  You can do this in the actions tab.


To make your cube zoom out when you rotate, goto "Rotate Cube" and change the zoom setting.  If you change "timestep", it will make the cube appear to bounce when it rotates.  Kinda hard to explain, but it gives it a cool effect.

You can also add a picture to the background when you rotate the cube.  This is called the skydome.  You can set it up in the "Desktop Cube" place, under the apearance tab.  Also, you can make your cube transparent in the transparency tab.  

Try playing around with these settings.  You can really customize your effects to your liking.

---

