---
title: "How to Install Icons??"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-03-11
I have downloaded a bunch of icon .zip files from deviantart.com and I am wondering how to install them? When I extract them, there are subfolders with the different types (they are .PNG) but I don't know how to install them as a icon theme. If I go into Themes>Icons and try to install the zip file it say s invalid file type.

Do I have to set them manually? If so, how the heck would I do that? Please help :confused:

---

### Post by Gerard Barberi on 2007-03-11
I believe you can stick the folders (unzipped) in the ".icons" directory in your home folder.  Just press control+h to view the folder and move the icons into there.

Or try archiving them in the proper format.  I think it's tar.gz

---

### Post by rocknrolf77 on 2007-03-11
Maybe it's easier to start installing the icons from [www.gnome-look.org](www.gnome-look.org)  They are archived in the right format. So you can download them and just drag the archives into the theme manager. :)

---

### Post by herbster on 2007-03-12
Gerard, that didn't work unfortunately :(

rocknrolf77, I have downloaded many icons from there but these are really exceptional icons I'd like to install.

Here is an example, please check it and see what I mean: [http://www.deviantart.com/deviation/10386634/](http://www.deviantart.com/deviation/10386634/)

If you click Download on the left you will get the .zip file and it has many subfolders, but no .theme file or nothing. There's got to be a way :(

---

### Post by herbster on 2007-03-12
Also, if you are to set manually the types of icons for say folders, trash, etc. individually (I mean you set the type of icon for a empty folder, and all empty folders use that icon, etc.) then where would you set these?

---

### Post by siciliancasanova on 2007-03-12
You might benefit from this.

Open up synaptic and make sure you have multiverse and universe selected and hit refresh.

Search "gnome-art"

It will place it as **System > Preferences > Art Manager**

Icons, Themes, Splash Screens, Login Screens, Wallpaper, etc...

---

### Post by Russty of Oz on 2007-03-12
You can install icons to be used by going to  System>Preferences>Theme>Theme Details  but I just tried that and the icons are in the wrong format.  However, if you want to use them for the desktop or files in your home folder etc.  you just need to right click on the icon you already have then Properties then click the icon showing in the Properties box and then find and select the one you want from the new file you have extracted.  I tried it and they are pretty cool looking icons!  I am sure there must be a way of changing them to the right format, the problem is I don't know what format they are suppose to be or how to do it.  Hopefully someone else may be know what format they need to be in and how to change it.

---

### Post by siciliancasanova on 2007-03-12
I would just get on gnome-look.org and download a few source files for some icon packages and see how they did it.

---

### Post by ramjet_1953 on 2007-03-12
If you create an additional directory in usr/share/icons (using gksu nautilus) and then unzip the icons into this directory, they will then be available. Give the directory a name to suit the icon set.

Then go to System>Preferences>Theme

Click on Theme Details and a window will open

Click on Icons and another window should open.

The new icon theme that you just installed should be listed.

If not, click on install and follow the prompts.

Regards,
Roger :cool:

---

### Post by herbster on 2007-03-12
> **ramjet_1953 said:**
> If you create an additional directory in usr/share/icons (using gksu nautilus) and then unzip the icons into this directory, they will then be available. Give the directory a name to suit the icon set.

Then go to System>Preferences>Theme

Click on Theme Details and a window will open

Click on Icons and another window should open.

The new icon theme that you just installed should be listed.

If not, click on install and follow the prompts.

Regards,
Roger :cool:

I have done this, but in the folder "soviet" which I have moved into usr/share/icons, there are subfolders like device, network, etc. but all have just .png files in them. So any file I click on and click Install it keeps saying file format invalid! :(

I think siciliancasanova is correct, I must find out how the icon theme makers make an icon theme and just copy them with these premade .png collections!!!! Anyone have any ideas or do I just ask the guys on gnome-look.org ??

---

### Post by Gerard Barberi on 2007-03-12
Yes, those are certainly beautiful icons and I can understand why you want them installed so bad.  

I'm at work, so unfortunately I'm on a Winbox:( .  When I get back I'll download them.

You could also try to put them into the /usr/share/icons directory and link individual launchers to them.

EDIT:  Looking inside the folders, it appears that the creator made a set of icons, not an "Icon Theme".  It's missing an index.theme file.

---

### Post by deviouskoopa on 2007-03-14
> **Russty of Oz said:**
> You can install icons to be used by going to  System>Preferences>Theme>Theme Details  but I just tried that and the icons are in the wrong format.  However, if you want to use them for the desktop or files in your home folder etc.  you just need to right click on the icon you already have then Properties then click the icon showing in the Properties box and then find and select the one you want from the new file you have extracted.  I tried it and they are pretty cool looking icons!  I am sure there must be a way of changing them to the right format, the problem is I don't know what format they are suppose to be or how to do it.  Hopefully someone else may be know what format they need to be in and how to change it.

Thanks a lot! I'm pretty new to Linux and found this helpful for installing my new cool glass icons: [http://www.gnome-look.org/content/show.php?content=32146]("http://www.gnome-look.org/content/show.php?content=32146")

---

