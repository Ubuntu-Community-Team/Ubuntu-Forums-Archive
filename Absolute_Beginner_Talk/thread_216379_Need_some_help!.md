---
title: "Need some help!"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by jkatana on 2006-07-15
ok.. i got wine... everytime i try to install world of warcraft my cd drive goes berzerk and wont eject... so i reset the power to it manualy.. put in disk 2 and it wont read it... so i try to download the client off blizard, you know no cds... the file manager is very uncompliant... so i look for a zip.. a huge zip.. i find 2 split rars.. i think close enough.. but 5.05 wont open it... i read 6.06 will so i update.. still cant open it! i try downloading winrar and try to use wine to operate it... it installs to a c drive and when i click run i get bump.. so im at my wits end where is wine installing all this crap to and how do i get to it is it permantent why cant i do this crap straight forward?!?!?!?! please note im on night three of no sleep till WoW... please help...](*,) PS after installing guild wars on my pc i cant get any depth in the game and laggs beond all known, and i cant get out of 600X800 resolution... its the only one on the list... how do i get Derect X on here too and fix my screen? PSS ok got the wine thing figured out found the directory of my stuff.. now i just need to fix the other crap..

---

### Post by rockfloyd on 2006-07-15
i don't know about the world of warcraft install stuff, but wine installs stuff to a hidden folder in the home folder. click view - show hidden files to find it.

---

### Post by skale on 2006-07-15
There's a long thread here, I haven't read it really. It applies to Gentoo, but should help anyway. 
[http://forums.gentoo.org/viewtopic-t-246098.html](http://forums.gentoo.org/viewtopic-t-246098.html)

---

### Post by catlett on 2006-07-15
You will have to be more specific if you want specific help. The main thing is "what is your system?" If you have a nvidia or ati card, "did you install the better drivers for it, not just what the install gave you?"
Compressed files are opened in Ubuntu by right-clicking on them and selecting "extract here". If you can't extract a winrar file , install rar. ```
sudo apt-get install rar
``````
sudo ln -fs /usr/bin/rar /usr/bin/unrar
```
Then post specific errors. What is happening. What is the output of the terminal after a command .

---

### Post by jkatana on 2006-07-15
OK update, i got world of warcraft installed, updated wine to 9.17, the cd thing was a bad connection,found all the installed stuff i couldnt, AND everything is peachy EXEPT... the frame rate is 3-4 per second, the models and textures are popping out all over the place,due to open GL which im going to take out the startup, and i cant target anything... theres a patch to the mouse thing the two things i need are how to up my rate, and apply the patch.. if someone can help me figure this out, me love you long time. i got 160 gb hdd, asus motherboard X, 128 on board video, 738 ram, 3.06 processor ubuntu 6.06

---

### Post by catlett on 2006-07-15
I can't tell what video card you have so I'll post both how to's. The better drivers will increase the frame rates.
For nvidia
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```
For ATI it's a little more work.
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
You need the extra repositories enabled to get access to the drivers. This is how if you haven't already [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

The instructions come from the Dapper Guide. It is a good thing to referrence when you need something  [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

