---
title: "Ubuntu and gnome-look.org"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Bright Hammer on 2007-10-24
Hi want to configure the look of my system by using some of the themes on gnome-look.org. So can some one help me with the following?

Where can I get a how-to’s on changing the look of my desktop?( when I have tried it never looks complete)

Is there a program to deal with the look of my desktop? (I am looking for something that handles customizing the look of grub, login screen, background …ect.)

Is there a way to import some ones compiz settings to my pc if I have a compatible video card?

---

### Post by reza81 on 2007-10-24
Take a look at:
System > Preferences > Appearance 

&

System > Preferences > Advanced desktop effects settings 


Have fun! :popcorn:

---

### Post by mikeyphi on 2007-10-24
Not exactly what you asked but this might give you some ideas: [http://ubuntuforums.org/showthread.php?t=490398](http://ubuntuforums.org/showthread.php?t=490398)

---

### Post by papercut on 2007-10-24
sudo apt-get install gnome-art

will get you an application that will let your browse what is available on art.gnome.org and automatically install it for you.  I found a couple of the options a bit buggy, but themes and wallpaper worked fine.

---

### Post by yabbies on 2007-10-24
when you download the theme you want off of gnome-look

go to system>preferences>appearances
on the themes tab there will be a "install theme" button or something like that
clicking that will bring up a search
browse to the place of your gnome-look download and and install the tarball 
it will automatically install your theme and make it current
then ask if you want to keep the current changes
if so, then you will have to give it a name to save the change.

have fun

---

### Post by reza81 on 2007-10-24
> 
Is there a way to import some ones compiz settings to my pc if I have a compatible video card?


You can do this to, unless some graphical settings are not compatible! Then it will properly crash or something. 

just copy ~/.gconf/apps/compiz/ 

dont forget to backup your own ~/.gconf/apps/compiz/

goodluck!

---

### Post by Bright Hammer on 2007-10-29
Thanks for all the Help. PaperCut that is exactly what I was looking for Thanks!

---

