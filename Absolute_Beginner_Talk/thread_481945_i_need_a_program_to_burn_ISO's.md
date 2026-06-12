---
title: "i need a program to burn ISO's"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Skillz_NoOdLeS on 2007-06-23
yea, i need a program to burn iso's

i would appreciate  if it was easy to install and stuff.

post here plz =)

---

### Post by Wake Rider on 2007-06-23
If you are using KDE then there is k3b.

sudo apt-get install k3b

Or on Gnome go to the package manager and look for Gnome Baker.

---

### Post by Skillz_NoOdLeS on 2007-06-23
im not sure if im useing kde.

im on ubuntu fiesty

---

### Post by Wake Rider on 2007-06-23
> **Skillz_NoOdLeS said:**
> im not sure if im useing kde.

im on ubuntu fiesty

Then you most likely have Gnome. There is a cd burning programme called Gnome Baker which you could try.

---

### Post by NeoLithium on 2007-06-23
GnomeBaker works well.  
```
sudo aptitude install gnomebaker
```

You may need to ensure that you have the additional repositories enabled. There's a guide to that (And many other programs) here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Easy to follow and will get you up and running quickly with a lot of things you might like.

---

### Post by Skillz_NoOdLeS on 2007-06-23
gnome baker  burns iso's  right?

---

### Post by gn2 on 2007-06-23
> **Skillz_NoOdLeS said:**
> im not sure if im useing kde.

im on ubuntu fiesty

Ubuntu uses Gnome, Kubuntu uses KDE.
.
You can install and use K3b, it's available through Synaptic Package Manager.
.
All the extra bits required to run K3b will be added for you. 
K3b is an excellent program and I highly recommend it.
.

---

### Post by kelvin spratt on 2007-06-23
there should be a program installed by default just right click on the image you want to burn near the bottom of the drogdown flag, you should see write to disc click on that you should then get ISO burner in the middle of the screen, inset disc of your choice ei cd, cd-rw, dvd, dvd-rw, your image is already mouted press burn that it
works for me.

---

### Post by Skillz_NoOdLeS on 2007-06-23
> **gn2 said:**
> Ubuntu uses Gnome, Kubuntu uses KDE.
.
You can install and use K3b, it's available through Synaptic Package Manager.
.
All the extra bits required to run K3b will be added for you. 
K3b is an excellent program and I highly recommend it.
.

whats synaptic package manager???

i know, i know.  i have alot a questions. =p

---

### Post by Crafty Kisses on 2007-06-23
> **Skillz_NoOdLeS said:**
> whats synaptic package manager???

i know, i know.  i have alot a questions. =p

It's the place where you get all your programs. :p

---

### Post by gn2 on 2007-06-23
> **Skillz_NoOdLeS said:**
> whats synaptic package manager???

i know, i know.  i have alot a questions. =p

[https://help.ubuntu.com/7.04/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.04/add-applications/C/advanced.html#synaptic)

---

### Post by Skillz_NoOdLeS on 2007-06-23
> **Codename said:**
> It's the place where you get all your programs. :p

hah, ok. 

but how would i get k3b useing it?

---

### Post by moredhel on 2007-06-23
do a search for k3b. then right click and install it. then click the apply button. :D

Also, there is brasero which is another cool burning program :D

---

### Post by Skillz_NoOdLeS on 2007-06-23
can u just give me something to copy and paste in my terminal?

its pretty apparent i don't know to much about linux =p

---

### Post by sunshine12 on 2007-06-23
option 1: 

As suggested above, Ubuntu has built in cdburner, just right mouse click your .ISO file and select "Write to Disk" option, i.e. second from below in drop down menu on right click..

Option 2: Press ALT+F2, and type gnome-terminal

this will open up terminal, make sure you have universe repositories enabled..
then copy , past following command..

sudo apt-get update
sudo apt-get install k3b

when install finishes, you will able to find k3b in ... Applications-sound and video-k3b

Hope this will be helpful...

---

### Post by ugm6hr on 2007-06-23
NeoLithium gave you a command for GnomeBaker - which will burn ISOs.

It will appear in your Multimedia menu (I think).  And it's dead easy to use.  

To burn an ISO in GnomeBaker - go to Tools Menu and select burn a CD image.

PS: If it won't install - open Synaptic Package Manager (in System Menu) - then go to Settings Menu and select Repositories and tick all the boxes in "Ubuntu Software" tab.

---

### Post by Skillz_NoOdLeS on 2007-06-23
oh, thanks guys =)

i appreciate your help =)

---

### Post by MrKlean on 2007-06-23
It's under .. Sysytem ...>..Administration.  It will let you install packages or programs that you want and need ; )

---

