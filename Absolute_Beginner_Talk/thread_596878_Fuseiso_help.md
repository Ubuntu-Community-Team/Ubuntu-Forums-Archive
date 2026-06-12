---
title: "Fuseiso help"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Elestat on 2007-10-30
Hi! i have been trying to get a .iso file to mount using fuseiso i write:

>  sudo fuseiso -p Doomsday.iso /media/do

according to the terminal everything is fine... (no error or anything). when i go to /media/ i see a do file but it doesn't appear as a directory but as a unknown file. so obviously i cant access it. what i am doing wrong ?. the .iso file is ok since i am able to mount it with the mount command. oh and i don't want to use acetoneiso so please don't tell me to use it.

maybe i am lacking some packet or something to use properly fuseiso or something like that. but i realy dont know since i am new to ubuntu and linux ! 
thx.

---

### Post by Elestat on 2007-10-30
I really need help guys.... anybody ?

---

### Post by bulletxt on 2007-10-30
you are a bit strange. you don't want to use AcetoneISo2 but  you want to mess around with CLI when you don't even know what are you doing.

anyways, tell me what exact version of fuseiso do you have.

---

### Post by thermans on 2007-11-21
Your user probably is not in the "fuse" group.

Using the command line:

> sudo nano /etc/group

find the line that starts with "fuse" and add your username to the end:

> fuse:x:106:username

Save and exit.  Then

> pwconv

If you'd rather use the GUI (on Gutsy), go to "System/Administration/Users and Groups".  Click on "Manage Groups".  Find the "fuse" group and click on "Properties".  Make sure your username is checked.

Log out and back in again.  

"fuseiso" should work now.

---

