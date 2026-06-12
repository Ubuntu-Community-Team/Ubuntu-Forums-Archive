---
title: "[SOLVED] Wine Menu Gone?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by akimatsu123 on 2008-03-27
Hi,

I uninstalled wine previously, but i thought i'd give it another try. Previously, when i uninstaller wine, it did not remove the wine menu under applications so i removed it manually. 

Now that i reinstalled wine, that menu won't come back, and so it's a pain in the butt for me to access the programs i installed. how do i get the wine menu under applications back? 

thanks

---

### Post by kesman on 2008-03-27
Open up synaptic package manager from system menu and search for wine with it. Mark it as "completely removed" and apply changes. After this, in terminal run 
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update

```
then remove directory .wine in your home and back in synaptic, install wine again. Maybe this helps.

---

### Post by akimatsu123 on 2008-03-27
i just tried that. it didn't help ):

---

### Post by akimatsu123 on 2008-03-27
I found a solution. I'll post it here just so that if anyone has the same problem they can go in and fix it. 

It seems that Ubuntu neglects to actually DELETE the menu potion from the application.menu file, but instead merely puts a <DELETED/> tag behind it to make it not appear. So whne i manually removed the wine menu, that's what happened. And even if i reinstalled wine the <DELETED/> tag remained there, and therefore the wine menu did not appear. 

So here is the solution. 

First of all, navigate to: **/home/<username>/.config/menus **

Then open the **applications.menu** file with gedit, or any other text editing software. The file is quite long, so it's better to just search (ctrl+f) for "deleted". You should see a tag that looks like **<DELETED/>**, and it should be precedented with a tag that says something like:

<MENU><NAME>wine-wine</NAME><DIRECTORY>something</DIRECTORY> etc. etc. just manually remove the <DELETED/> tag, and save.

Now right click on the menu bar, choose edit menu. Under application, you should once agian see a wine. Check the box, and you're good to go :D

---

