---
title: "Problem placing new OpenOffice Icons"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-07-04
Hi,
After seeing how much better the icons for the windows version of OpenOffice are than the ones for the Linux version are, I've proceeded to make my own icons. 

I'm doing this in a sort of round-about way and it partially works, but I'm running into a snag. I'm right-clicking my panel and choosing 'Add to Panel' and creating a custom application launcher. 

Before this I place my new icon in the usr/share/pixmaps folder, so I can access the icon from the custom application launcher. When I create my custom application launcher, I'm using the same command that the respective Ooffice icon has like this:

```
ooffice -writer%U
```

So this works and the icon gets added to the panel. Then I drag it out onto my desktop, and everything is fine until I try to do a second Ooffice icon (say, the spreadsheet program icon, for example). When I do the 2nd icon and try to drag it onto the desktop, a windos pops up and says

"Ooffice.desktop already in place/Skip or Replace"

And if I replace, it replaces the 1st icon I just created even though it's a different program !!

This has happened 3 times and then one time, the 2nd icon worked correctly without erasing the other icon and I don't know why.

I appreciate any assistance on this if possible,

Many Thanks,...Frank B.

---

### Post by Computer-Slave on 2007-07-04
I guess icon names are conflicting try to keep different names of each icon.

---

### Post by abn91c on 2007-07-04
the widows version icons are on linux, right click on the icon>properties, the click on the icon image, this will bring up the icon repositories, then just search for office icons

---

### Post by Brightbelt on 2007-07-04
Thanks Abn, but following your instructions, I double-click on the icon in the properties window and all I get is my own file system/Documents directory. I get No Icon repository. Or if the (windows vs) open office icons are in my file system somewhere, I don't know the folder/directory in which to search. 

I could be doing something wrong, but what?

Computer-slave, that is certainly a logical suggestion, but the icons are already named differently.   

Many Thanks for helping; I'm open to any suggestions,....Thanks, Frank B.

---

### Post by abn91c on 2007-07-06
i use kubuntu, if i right click on the icon i get the windows-like menu, if i go to properties then i click on the icon picture, then i get all the system icons, the i select the other office icon

---

### Post by Brightbelt on 2007-07-07
Yes, I'm on Gnome, so I have to learn where to look. I've found some icons in the opt/cxoffice/share/icons folder, but not the windows system versions icons I'm looking for.

Knowing that directory, at least, allows me to put my own icons there and do the switch to my own icons rather easily.

If you're interested, I've attached icons which I have created for Oos here....I did them in Photoshop 7.0 on wine.

Many Thanks again, Frank B.

---

### Post by lluisanunez on 2007-07-07
I don't know about adding your own icons, but I believe OpenOffice syncs theme with your desktop theme. I have Industrial Tango theme on Gnome, my OO looked very ugly till I installed Industrial Tango for OO. Themes are found in synaptic -search for openoffice.org-style

---

### Post by Brightbelt on 2007-07-07
Thanks Lluis - I installed Tango. But when I go to Sytem/Preferences/Theme and don't know where to browse to find the Tango theme I just installed.

Could you point to where the directory is for that? 

I appreciate your assistance here,. Frank B.

---

### Post by Brightbelt on 2007-07-07
It looks like this requires Compiz to be installed, which in turn requires one's advanced acceleration graphics driver to be installed. 

I'm on an older Gateway M675x laptop and I was able to get my preferred resolution by using Envy to install my ATI card. But the ATI card or Linux apparently does not support the accelerated graphics in this case. 

However, correct me if I'm wrong. It seems this should not stop me from being able to get a better desktop shortcut icon for open office.

Thanks, Frank B.

---

### Post by lluisanunez on 2007-07-07
System >> preferences >> theme >> customize >> icons

---

### Post by AlexenderReez on 2007-07-07
how about look at this icons...cute right?


> [http://www.gnome-look.org/content/show.php/OpenOffice+Icons?content=61799](http://www.gnome-look.org/content/show.php/OpenOffice+Icons?content=61799)

---

### Post by lluisanunez on 2007-07-07
Oh, are you trying to get a shortcut icon? That's easy:
* create your icons (best in png format) and put them in a /icons directory under your home folder
* right click on the shortcut >> properties >> clic on the icon
* navigate to  /home and select the /icons subdirectory

---

