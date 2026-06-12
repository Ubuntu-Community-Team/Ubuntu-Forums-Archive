---
title: "Folder icons"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by yanewby on 2006-07-17
Day 3 in Ubuntu and still loving it!

One query I have have not yet been able to solve is one involving folder icons. 

I have a number of folders that I would like to have a special icon displayed instead of the default orange (in the human theme) folder icon.

In Windows it was a simple matter to change the icon of a folder using a .ini file.  Alternatively in thumbnails view, placing an image called folder.jpg into the folder would change the folder icon to that of folder.jpg (instead of the default one).  For instance, if I had a folder full of Gnarls Barkley music and I placed an image of Gnarls called folder.jpg in the folder, the picture of Gnarls would be displayed as the folder icon instead of the default icon.

Is there any way of doing this in Ubuntu?

---

### Post by adam.tropics on 2006-07-17
right click on the folder cocerned, go to properties, and click on the folder image. It will give you a file selection window from where you can navigate to the image you wish to use instead. Also in properties, have a look at emblems, these could prove more helpful for what you're after.

---

### Post by yanewby on 2006-07-17
Thank-you so much!  I knew this must be something easy like this but just couldn't see it...

Is there an easy way to restrict the sizes of the icons on the desktop?

---

### Post by Perfect Storm on 2006-07-17
You can right click it on the desktop and choose resize.

---

### Post by adam.tropics on 2006-07-17
well you can stretch them, again, the right click menu. And also you can set the default size by running configuration editor (gconf-editor in terminal), and following the menu to...

apps>>nautilus>>icon_view

where it says default_zoom_level, change to small, smaller, or large....I'm sure there are others, but I don't know them off the top of my head!

---

### Post by yanewby on 2006-07-17
Thanks again adam.tropics!  Your comments guided me in the right direction.

---

### Post by NinjitsuStylee on 2006-07-30
Actually I find that if I hold down control and move my scrollwheel, it changes the zoom level automagically.

Now here's the million-dollar-question:

How do I change the icons of LOTS of these folders automagically without having to right click each and every single one of them?  Somebody has to know of some bash scripting to do this.....

I just want to set the icons of every folder in my music directory to its respective Folder.jpg file (ie if the folder is Music/Dream Theater - Octavarium then the file it should look for is Music/Dream Theater - Octavarium/Folder.jpg and the icon for Music/Dream Theater - Octavarium should become that Folder.jpg...........and it needs to do this for LOTS of folder).

---

### Post by confused57 on 2006-07-30
Could you hold down the Ctrl key, then left click the folders you want to change...then right click one of the highlighted folders and make changes?

---

### Post by NinjitsuStylee on 2006-07-30
> **confused57 said:**
> Could you hold down the Ctrl key, then left click the folders you want to change...then right click one of the highlighted folders and make changes?

No, because this would change the icons of the folders you've selected to one jpg file.  We want to change the icons to their OWN jpg files.

In other words, your method would make folders alpha, beta, and gamma all use the icon of the alpha folder.  We want alpha to use its own Folder.jpg, beta to use its own Folder.jpg, etc.

I've been hunting down resources for this to no avail.  I've even tried messing with the .nautilus/metafiles/ XML data and that seems to do absolutely nothing.  

Anyone know anything about this?

---

