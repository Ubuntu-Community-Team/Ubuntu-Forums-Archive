---
title: "Default Wallpaper folder for Ubuntu...."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-18
I have a wallpaper collection I'd like to transfer over to my Ubuntu box. Normally when I do this on a Windows Box I just browse to "C:\Windows\Web\Wallpaper" and drop my collection in there. Does Ubuntu have a similar "system folder" for storing the default wallpapers?

---

### Post by oscar on 2006-06-18
/usr/share/backgrounds/ seems to be the place but to get them in the list by default for all users it looks like you have to edit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml

---

### Post by mlind on 2006-06-18
If you just need to use the wallpaper locally, put it anywhere on your home folder and
just use "Add Wallpaper" option on gnome-background-properties.

---

### Post by ZeusABJ on 2006-06-18
Yeah MLind, I knew you could do it that way. I was just hoping that by dropping them in the default folder I would not have to actually have to "install" them. However if Oscar is correct i have no other alternative. Oh well, its probably better that way.

---

### Post by Cetus on 2007-06-10
I apologize in advance for the long post...
(This is valid for Ubuntu 7.04, Feisty Fawn, but I presume it will work for other versions also..)

Taking oscar's tip, this is step-by-step what I did to get images in the 'list' :

   As root: (sudo)
(1) Move or copy the images you want to the /usr/share/backgrounds/ folder. 
(e.g To move or copy the images you want to the correct folder from your desktop:
(Terminal window -->) :~$ sudo cp /home/[your name]/Desktop/*.jpg /usr/share/backgrounds/   
...simple as that! (Note very important space between ...*.jpg and /usr/share...
i.e. ...*.jpg[space]/usr/share...)

   Note: Use 'mv' instead of 'cp' if you want to 'move' (versus 'copy') the files to the backgrounds folder. 
Also, use the correct file extension for the images to be moved or copied 
In my example note that I used '*.jpg', meaning 'all files that end with '.jpg'
For example, if the files are of '.png' type, use '*.png' instead...

   To get them in the list by default for all users (the 'list' as in the Desktop Wallpaper list, 
when you right-click on desktop and select 'Change Desktop Background'):
(2) Edit (as root, using the existing entries as a template)  /usr/share/gnome-background-properties/ubuntu-wallpapers.xml
(e.g. sudo gedit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml)

---OR---

   Simply put the images in any folder (preferably somewhere in your 
'home' folder, right-click on the desktop, choose 'Change
Desktop Background', click the 'Add Wallpaper' button, and browse to the 
folder where you put your images and select one. 

Viola!

---

### Post by ZeusABJ on 2007-11-23
Sorry I have not responded sooner. Thank you very much for your "HowTo". It is greatly appreciated.

---

