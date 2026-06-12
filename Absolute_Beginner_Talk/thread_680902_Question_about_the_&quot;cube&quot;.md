---
title: "Question about the &quot;cube&quot;"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Teh-Shewz on 2008-01-28
What do i need to get the cube
is it dled with the ubuntu cd or do i need to get it some were else
these are the compiz files i have.

compiz
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins

i dont even kow if compiz has anything to do with it but help me por favor.

---

### Post by LaRoza on 2008-01-28
> **Teh-Shewz said:**
> What do i need to get the cube
is it dled with the ubuntu cd or do i need to get it some were else
these are the compiz files i have.

compiz
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins

i dont even kow if compiz has anything to do with it but help me por favor.

compizconfig-setting-manager 

is needed to customize it. After installing, it will be under System->Preferenced->Advanced Desktop Effects Settings

---

### Post by Teh-Shewz on 2008-01-28
were can i get compizconfig-manager

---

### Post by ~LoKe on 2008-01-28
> **Teh-Shewz said:**
> were can i get compizconfig-manager

```
sudo apt-get install compizconfig-settings-manager
```
Should do the trick.

---

### Post by lswest on 2008-01-28
you can get it by running ```
sudo apt-get install compizconfig-setting-manager
```

---

### Post by Teh-Shewz on 2008-01-28
this is what i get

 sudo apt-get install compizconfig-settings-manager
[sudo] password for jimmy:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
jimmy@jimmy-laptop:~$

---

### Post by lswest on 2008-01-28
search for the right package name with ```
sudo apt-cache search compizconfig
```  also, try running ```
sudo apt-get update
``` before installing.

and lastly, check to make sure your repos are right under system-->administration-->software sources.  make sure universe and multiverse are checked, and the CD unchecked.

---

### Post by emarkd on 2008-01-28
Have you enabled the extra repositories?

System > Administration > Synaptic

Then click on the Settings > Repositories menu.  Check all of the boxes except Source Code.  Save it and click the "Reload" button on the main screen.  Then try your install command again.

---

### Post by Teh-Shewz on 2008-01-28
k thanks and one last question hahah
i have the advanced d top
nhow to i enable the cube 
i c the options for it witch ones should i pic

---

