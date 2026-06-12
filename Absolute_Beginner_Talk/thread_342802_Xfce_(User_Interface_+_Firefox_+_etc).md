---
title: "Xfce (User Interface + Firefox + etc)"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-20
So I'm using the xfce-dusk theme and I quite like it, but right now I have to type this is my text editor and then paste it into the forum because my text color is white!!!

Sometimes I'm lucky and text fields are black but not in this case.

So I was wondering is there a way to make the web pages on Firefox ignore the xfce-dusk settings? I really don't want to give up the theme.


Next thing. I installed the thunar-archive-plugin, but when I try to extract or archive anything I get "No suitable archive manager found". xarchiver was installed at the same time as a dependency. What do I need to do to make this work?


When I go into "Desktop Preferences" and tick "Allow Xfce to manage the desktop" it prompts "To ensure that Xfce does not manage your desktop the next time you start Xfce, please be sure to save your session when logging out. If you are not using the Xfce Session Manager (xfce4-session), you will need to manually edit your ~/.conf/xfce4/xinitc file ... etc" I want Xfce to manager my desktop! when I reboot I don't save my session and it gets disabled. How do I resolve this?


Also does anyone know where you can find some good usplash themes?


Any help would be awesome.


Note: I did not install xubuntu, but a command line system and then installed xfce etc. And using Edgy.

---

### Post by bonzodog on 2007-01-20
This is a common problem with dark gtk themes - I have found that one way around the problem is to change Firefoxes colour settings (Edit --> Preferences --> Content Tab --> Colors). What you can do is untick 'allow web pages to set their own colors' the downside to this is that you lose the forums CSS, and the webpages will use a dark background, and some CSS set images will disappear. fiddle around with FF's color settings.

---

### Post by guysmiley25 on 2007-01-20
Chears for that bonzodog. I found an option "Use System Colors" and I unticked that. That helped alots but with the "Allow pages to choose their own colors, instead of my selections above" I would rather leave checked for the reason you meantioned. So I'm still at a stand still!!!

If I do decide to change my theme does anyone know where I can find some cool looking ones?

---

### Post by guysmiley25 on 2007-01-20
Bump!

---

### Post by euler_fan on 2007-01-20
> **guysmiley25 said:**
> Chears for that bonzodog. I found an option "Use System Colors" and I unticked that. That helped alots but with the "Allow pages to choose their own colors, instead of my selections above" I would rather leave checked for the reason you meantioned. So I'm still at a stand still!!!

If I do decide to change my theme does anyone know where I can find some cool looking ones?

google xfce-look and gnome-look. gnome-look especially has a wide array of amazing themes. With XFCE you'll need to grab the GTK 2.x themes, download them to the desktop, untar them to a folder I will call "themes "and then go into the terminal and do the following:

cd ~/Desktop/themes
ls
sudo mv theme1 /usr/share/themes

Repeat the last line over and over again until all the folders you unpacked to the themes folder on your desktop are in the /usr/share/themes folder. You can do the same thing for icons but change

sudo mv theme1 /usr/share/themes to sudo mv icons1 /usr/share/icons after unpacking the icons to ~/Desktop/icons and running the command cd ~/Desktop/icons

Unfortunately insofar as I know that is the only way to get more themes into Xfce. It is not quite as easy as with Gnome. Can't comment on KDE, have never tried it.

---

### Post by guysmiley25 on 2007-01-21
Chears euler_fan I have in the end given up on dark themes :( but there are other cool ones out there.

As for my thunar-archive-plugin and "Allow Xfce to manage the desktop" problems I have solved them.

First I logged out and saved my session and then logged back in, then logged out not saving my session cause thats how I like it. And that seemed to solve both problems.

As for the usplash themes does anyone know? xfce-look, gnome-look, etc Do not have much in this way.

Thanks heaps bonzodog and euler_fan

---

### Post by euler_fan on 2007-01-21
No problem. Glad to do it. :D

---

### Post by leoakch on 2007-03-02
Hello guysmile25, i also really like some dark themes like xfce-dusk, i had the same problems with dark themes in the past.
To solve follow this instructions : 

-Download the Neutronium theme : [http://www.xfce-look.org/content/show.php?content=46153](http://www.xfce-look.org/content/show.php?content=46153)
-Open/extract this file : ./Neutronium-Theme-Pack/Neutronium-GTK2/instructions.txt

Following this instructions my firefox seems to be fine :)


I hope this helps.

---

### Post by guysmiley25 on 2007-03-02
Thanks heaps for that it worked well!

Is that like a default css file, where the css file for a webpage would over write that one?

---

