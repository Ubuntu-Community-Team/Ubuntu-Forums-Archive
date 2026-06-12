---
title: "How do i uninstall Programs and wine programs"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by BluePlum on 2008-03-04
How do i uninstall wine Programs And Normal programs.

Kiba-dock Didn't install right due to a repository Problem and no one will help me so need uninstall it.

And when i click uninstall wine program it doesn't uninstall or show the programs.

---

### Post by spiderbatdad on 2008-03-04
you could try this method:```


cd kiba-dock/kiba-dbus-plugins
sudo make uninstall
cd ..

cd kiba-dock/kiba-plugins
sudo make uninstall
cd..

cd kiba-dock/kiba-dock
sudo make uninstall
cd..

cd kiba-dock/akamaru
sudo make uninstall


```

It really depends on how you installed it. You could try
```
sudo dpkg -r kiba-dock
``` You could locate and delete all files related to kiba dock, but be careful you don't ruin your system. see this thread, and poke around a little more before breaking anything: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by BluePlum on 2008-03-07
How do i uninstall the wine programs tho?

---

### Post by Bri0 on 2008-03-07
I believe its: 

Applications > Wine > uninstall wine programs

Tho there is a problem when uninstalling Wine programs, is that the program you uninstall may still be in its Wine menu. So to remove those unwanted menus is to go into 'System' > 'Main Menu' to just hide them. Hopefully they will get this fixed.


To uninstall the Wine program go into Synaptic.

---

### Post by BluePlum on 2008-03-07
you cant hide anything in the wine program folder Sadness... And that first post to uninstall kiba dock did not work

---

### Post by x05 on 2008-03-08
You could try:
```
sudo apt-get remove <enter package nane>
```

Put the package name you want gone in the <enter package name>

---

