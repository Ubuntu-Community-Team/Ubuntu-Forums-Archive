---
title: "[SOLVED] Modifing Ubuntu"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by tbrminsanity on 2007-01-12
I used Xubuntu for the last 6 months and I love it but recently I moved to Ubuntu 6.10 and I have been stuck on something.  In Xubuntu I was able to change where I wanted to place the min, max, close, and menu buttons on the windows.  I grew up on an Amiga and I like my close button in the top left corner of each window.  How do I do this in Ubuntu?

This is what I have:
[IMG]http://www.geocities.com/tbrminsanity/now.png[/IMG]

And this is what I want:
[IMG]http://www.geocities.com/tbrminsanity/amigawindow.png[/IMG]

---

### Post by dca on 2007-01-12
By going to gnome-look.org you can d/l & install newer themes available to gnome...  Some of the OSX-looking themes have that on the left...

---

### Post by tbrminsanity on 2007-01-12
Ive tried using those themes and the close button is still on the right.

---

### Post by Tomosaur on 2007-01-12
The little icon in the top left is actually a button. If you click it a little menu should appear, one of the options is to close. Not as quick as you want, but it should tide you over. I personally don't know any way of moving the close buttons.

---

### Post by xael on 2007-01-12
Hello friend,

Have you tried Kubuntu?. KDE often includes several window decorations that intent to clone other systems, maybe you can find one you like there.

---

### Post by blackened on 2007-01-12
This method isn't very user friendly.  Go to either /home/*username*/.themes/*themename* or /usr/themes/*themename* depending on how you installed the theme. From there you can find and edit the metacity.xml configuration file and change the coordinates for the individual buttons.

---

### Post by tbrminsanity on 2007-01-12
> **blackened said:**
> This method isn't very user friendly.  Go to either /home/*username*/.themes/*themename* or /usr/themes/*themename* depending on how you installed the theme. From there you can find and edit the metacity.xml configuration file and change the coordinates for the individual buttons.

I was looking in that file but I'm not sure what tags do what.  I will play with it and post my results.

---

### Post by tbrminsanity on 2007-01-12
> **xael said:**
> Hello friend,

Have you tried Kubuntu?. KDE often includes several window decorations that intent to clone other systems, maybe you can find one you like there.

I have tried KDE but not Kubuntu.  I like Ubuntu and find it easier to find How-tos for Ubuntu over Kubuntu so I would like to stay with Ubuntu.  If all else fails I know how to modify the window with Xfce and can switch to Xubuntu and just enable GDM and KDE services.

---

### Post by tbrminsanity on 2007-01-12
> **Tomosaur said:**
> The little icon in the top left is actually a button. If you click it a little menu should appear, one of the options is to close. Not as quick as you want, but it should tide you over. I personally don't know any way of moving the close buttons.

Is there a way to set the menu so that double click will close the window?  It does that in Windows but not in Gnome I don't think.

---

### Post by blackened on 2007-01-12
If you'll point me to where you found the theme I can take a look and see about modifying it the way you want it.
Or pm me and you can email it.

---

### Post by Tomosaur on 2007-01-12
Found it!

Open up a terminal, and type 'gconf-editor', and press enter.
In the left hand panel, click 'apps', then find 'metacity', then, 'general'.
In the right hand panel, you should see a line which says 'button_layout'. Double click it and erase the existing line, and paste this one in its place:
'close:minimize,maximize,menu'

The colon seperates the left hand corner from the right hand corner. You can choose to leave out an option if you so wish.

---

### Post by blackened on 2007-01-12
Ah well done. That's much easier than editing the metacity file.

---

### Post by tbrminsanity on 2007-01-12
Thanks it works like a charm.

---

