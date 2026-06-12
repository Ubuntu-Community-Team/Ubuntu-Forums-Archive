---
title: "Updating to Dapper from Hoary"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2006-07-06
Hey, I'm still on Hoary at the moment and would like to update to Dapper. How is this possible without downloading an iso or ordering from shipit?

Thanks in advance,
Kris

---

### Post by ajgreeny on 2006-07-06
Your user CP suggests you are a Breezy user, though this may just be a mistake.  In theory this shouldn't matter and you can do an upgrade using apt-get, but from what I've read in several posts, it may not be wise to try to jump two versions in one go, ie from Hoary to Dapper; it could be just one jump too far.  On the other hand if you've backed everything up you haven't got much to lose.

If it were me I would download the new iso and start afresh.  Whatever you chose - Good Luck!

---

### Post by KrisDwyer on 2006-07-06
How would i go about jumping from Hoary to Breezy then (Breezy worked fine on my PC) using apt?

Thanks,
Kris

---

### Post by ajgreeny on 2006-07-06
I suggest you have a look at the following site which has a lot of information on such things you have asked about, and much more.  Bookmark it on your browser and you will find it very useful.



You need to do the following to upgrade from one version to another, though bear in mind this is for breezy to dapper.  For your situation it would mean changing the references to hoary and breezy:-

1  Change your sources.list First, back them up. sudo cp /etc/apt/sources.list /etc/apt/sources_breezy.list 
Then, if you're using Gnome gksudo gedit /etc/apt/sources.list
 If you're using KDE kdesu kwrite /etc/apt/sources.list
 If you're using XFCE gksudo mousepad /etc/apt/sources.list
 Once the sources.list file is open, do a find/replace--finding the word *breezy* and replacing it with the word *dapper*. Save the file.



2  Exit whatever desktop environment you're using. Go back to the log in screen. Then press Control-Alt-F1. This will take you to a text-based login. Log in and then type
 sudo aptitude update
 sudo aptitude dist-upgrade


3  You don't need to reboot (sudo reboot), but it may be a good idea. If you prefer not to reboot once the upgrade to Dapper is done, press Control-Alt-F1, then Control-Alt-Backspace. Then log in. 
 
     
 
4  Good luck if you try it.

---

### Post by KrisDwyer on 2006-07-06
What was the website?

---

### Post by KrisDwyer on 2006-07-06
Also, how big is the update usually? :neutral:

---

### Post by insane_alien on 2006-07-06
it will take maybe an hour or two depending on your internet connection. just follow ajgreeny's step by step thing and it should work. back up just incase though.

---

### Post by nico1278 on 2006-07-06
I updated from clean hoary -> breezy -> dapper and it works w/o any promblems.

---

### Post by drayan69 on 2006-07-07
Can you please explain in detail how u upgraded using Dapper CDs?

I tried using conventional way using synaptic, changing all instances of Breezy to Dapper in sources.list file and adding CDrom to repository.

The message comes unable to mount CD. 

CD is fine and my Combo drive is also working fine. I am stuck..](*,) please help

---

### Post by nico1278 on 2006-07-07
I don't quite understand what is the problem. Change all breezy to dapper in you sources and update :

sudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

In general, you don't really need the CD in your sources if you have a good internet conection, so you can just skip it.

---

