---
title: "HELP - I messed something up!"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2007-01-10
Ok, I'm using 6.06 and I tried to install Automatix2 from instructions I found on the web. Unfortunately, I installed the wrong version, one for the latest version (Edgy?) or 6.10 (I prefer using the version numbers. Its easier than remembering these strange names)

So I tried Synaptic and I get the following message:
> 
E: Type '“deb' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I know this has to do with my borked Automatix2 install so I use the file system to open /etc/apt/sources.list and delete line 36 but when I try to save it, the system tells me I don't have the permissions to do so. 

How do I get these "permission"? I'm the only one who uses this system and have only one password set up when I boot into the thing. I'm between a rock and a hard place. I can't seem to uninstall the wrong Automatix and I can use neither Synaptic or Add/Remove because of this messed up sources.list file, which I can't seem to change without the proper permissions. ](*,) 

Apparently, I'm permitted to mess up the sources list, just not fix it. :???:

---

### Post by bigken on 2007-01-10
in a terminal type sudo gedit /etc/apt/sources.list then you can edit and save

applications/accessories/terminal

---

### Post by Sef on 2007-01-10
> in a terminal type sudo gedit /etc/apt/sources.list then you can edit and save

1) Type **gksudo** gedit /etc/apt/sources.list.   If you type sudo, you may create other problems.  

2) copy and paste your sources list here, if you are unsure of what to do.

---

### Post by atarileaf on 2007-01-10
Thanks guys. I've successfully undone my stupid mistake. Oy, lots to learn.
Thanks so much!

---

### Post by bigken on 2007-01-10
[quote=Sef;1993243]1) Type **gksudo** gedit /etc/apt/sources.list.   If you type sudo, you may create other problems.  


Can explain what the difference is and what problems it may create ?

just that I have always used sudo :-k

---

### Post by usien on 2007-01-10
just 4 the reference,if nyone ever needs it.instead of typing in the terminal for modifying more than one file, u can start the file browser as the root in gnome by typing this in the terminal:
sudo nautilus

then u can make ny modifications to ny files without doing nything else

---

### Post by Modernity on 2007-01-10
ALSO, for newcomers, your install to Ubuntu doesn't create a ROOT password, hence the use for "sudo". It's just my opinion, but after install it would be a good idea to change the root password to something different than your account password. (PLease ask how to do this before attempting, if you don't know how). That way, if you do mess up the permissions, you don't get completely locked out of root, if sudo stops working.

---

