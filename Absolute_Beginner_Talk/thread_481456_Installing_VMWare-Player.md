---
title: "Installing VMWare-Player"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by viseversa on 2007-06-22
I just got my copy of Ubuntu, and I am completely new to the linux O/S. I downloaded a copy of VMWare-Player but I have no clue how to install it. Could someone please tell me step by step what I have to do to install it, or any other program I may install in the future for that matter? Thanks in advance...

---

### Post by forestpixie on 2007-06-22
The easiest way to get VMWare is through synaptic - System>Admin>Synaptic Package - search for program - mark for installation and it'll install for you.

And welcome!

---

### Post by viseversa on 2007-06-22
Well, the version in Synaptic Package Manager is out of date, I need 2.0 so I downloaded it myself. Is there a way I can get Synaptic Package Manager to update it for me?

---

### Post by Motoxrdude on 2007-06-22
Is the file a .run file?
Move the file to your "Home" folder.
You can install it by going to the terminal (Applications>>Accesories>>Terminal)
type
```
sudo ./(name of the file).run
```
Enter in your password (when typing your password, nothing will be displayed, this is norma).
Just accept the defaults (just keep pressing enter).

Or you can install it by entering this into the terminal
```
sudo apt-get install vmware-player
```

---

### Post by viseversa on 2007-06-22
No, it started as a tar file but I extracted it to desktop, theres a vmware-player-install.pl file. When I try to run it in terminal it says "Please rerun this program as the super user." Also if I try to move any file into the Home folder it says "You do not have permission....."

---

### Post by forestpixie on 2007-06-22
super user is su, sudo is super user do

i think that's the terminology

---

### Post by viseversa on 2007-06-22
I got it guys, thanks to you. Thanks a million

Wait, during installtion i get this problem...

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware/modules/source/vmmon.tar" file in the 
"/tmp/vmware-config0" directory.

---

### Post by Adrian on 2007-06-22
:Dwhy not forget vmware altogether my freind and use wubi instead the beauty of wubi is that when you download it the programme is already a virtual copy of ubuntu feisty fawn this means that you dont need to install set up partitions in fact you can boot up or windows or ubuntu (windows being the default) and then if you dont like it just go into add remove programmes on windows and delete it like any other file...try it its free ...and no it wont damage your windows installation.....look up wubi on your search engine  best wishes Adrian

---

### Post by Motoxrdude on 2007-06-22
> **viseversa said:**
> I got it guys, thanks to you. Thanks a million

Wait, during installtion i get this problem...

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware/modules/source/vmmon.tar" file in the 
"/tmp/vmware-config0" directory.

Just run
```
sudo apt-get install vmware-player
```
and see if you have any more luck that way.

---

### Post by viseversa on 2007-06-22
Well, that installs VMWare Player but it's a older version and on my windows vista I have the newer version of the workstation so I can run it in a older version of the player, I need to install VMWare player 2.0 and that only installs 1.0 =(

---

