---
title: "share files with XP"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2005-11-23
hi all
Im trying to share files between my ubuntu PC and my XP laptop who are both behind a router. 
I set up a samba server and i can see and modify files on my XP  But from the XP side I cant access Ubuntu. I can't see any shared files in XP's 'my network places' (even though i specifically created several shred files on ubuntu which have the letters SMB on their icon so i assume it shows they are Samba files).  On XP's 'show workgroup computers' I cant see Ubuntu but when i click on it ,it says access denied , I don't have the permission or the parameter is incorrect.
I think it must some security issue but i can't see how to configure Samba. I can't find it anywhere in Ubuntu. I checked places>network servers . I found 4 icons : Ubuntu , XP , a shared file (on Ubuntu) and something called 'Windows Network'. In all four there is no configuration option. Except perhaps the properties tab which are all set to 'read only' but since the ownership belongs to root i can't change it (i don't know how to do it thru the terminal)
Any advices?

---

### Post by kperkins on 2005-11-23
My advice is to install swat (the webbrowser-based graphical frontend for samba) and the samba-doc package.  
You can also try using System >Administration > Shared Folders from the main menu, but I haven't tried it, since I set up my samba.conf manually, so I'm not sure if that'll help your problem or not.  I set up my sambe to use shares, instead of users for access, which makes it easier (though less secure) to access computers on the network.

---

### Post by seshomaru samma on 2005-11-25
I sudo apt-get install swat, but can't find it anywhere:confused:

---

### Post by oskude on 2005-11-25
its in "universe", see [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by matthewv on 2005-11-25
[QUOTE=seshomaru samma]I sudo apt-get install swat, but can't find it anywhere:confused:[/QUOTE]
swat is a web based config app. To use it goto [http://localhost:901/](http://localhost:901/)

---

### Post by xelink on 2005-11-25
try creating a fat32 partition... if you already have one, but can't use it on ubuntu, check ubuntuguide  [http://ubuntuguide.org/](http://ubuntuguide.org/)

that site has helped me tremendously.

---

### Post by seshomaru samma on 2005-11-25
[QUOTE=matthewv]swat is a web based config app. To use it goto [http://localhost:901/](http://localhost:901/)[/QUOTE]

The conection was refused!

I thought maybe it didnt install properly so i apt-get again but it says :

> swat is already the newest version.

---

### Post by matthewv on 2005-11-25
You probably need to start swat first. Try running ```
man swat
``` for a   bit more help. I think that includes something on that.

---

### Post by Chayak on 2005-11-25
I had a similar issue.  I went to SYSTEM>ADMINISTRATION>Shared Folders and turned on an SMB share.  I could see it and connect to it with my game laptop (winXP) but it wouldn't accept my user name or password.  I've set up shares numerous times before on Redhat/Fedora and not had any issues.  Is there something I'm missing in Ubuntu? (5.10 on this system) I have everything installed, it just won't accept my login.

---

### Post by snowjunkie on 2005-12-01
You need to add your username to the samba users list.  I forget the command - it's smbpwd -a username or something like that...

---

