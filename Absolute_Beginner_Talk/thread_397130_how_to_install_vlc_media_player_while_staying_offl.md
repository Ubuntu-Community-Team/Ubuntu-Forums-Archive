---
title: "how to install vlc media player while staying offline ?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by saiinch on 2007-03-30
first of all i would like to thank every poster here, those who question(s) and to those who give answers, thank you so much, without you ppls we beginners could never solve our problems, specially me.
The question i want to ask, is that, i want to install vlc media player in my ubuntu edgy 6.10 but i do not have internet connection in ubuntu because i am using wireless connection so it works in xp (btw i am on dual boot, with the help of ubuntu forum member, thanks again) anyway, now i want to install vlc media player, is it possible to install vlc media player in offline mode and is it possible to backup all the downloaded softwares ?

---

### Post by Schalken on 2007-03-30
download the libvlc0, vlc and vlc-nox packages from packages.ubuntu.com in windows, transfer em to ubuntu, double click on them and install.

you may have to download any dependancies one by one. im not sure how you can do that quickly. the whole software repo idea is based on being connected to the internet :P

---

### Post by saiinch on 2007-03-31
i have downloaded all these packages, i downloaded all from vlc recommended site which is "ftp://ftp.videolan.org/pub/videolan/ubuntu/pool/vlc/0.8.6a-jb/" after downloading i write them on a cd and in ubuntu i tried to add the cd in repositories but nothing happens except getting errors, i even installed easy ubuntu and automatix but they both need internet access which i dont have in ubuntu, now i want to uninstall easy ubuntu, how can i uninstall easy ubuntu and install vlc player in offline mode without internet connection AT ALL !!

---

### Post by seshomaru samma on 2007-03-31
you dont need to add them as repos
just copy them to a directory like /tmp or /home and double click on them

---

### Post by saiinch on 2007-04-01
i tried to copy all packages on cd and then run from cd but this didn't work as well, second thing i got to know on this forum, some thing like

sudo aptitude clean


sudo aptitude update
sudo aptitude install vlc


cd ~/desktop
sudo dpkg -i *.deb

but i am stilling getting errors which says that some packages cannot be unpacked (something like that i dont remember) and it says that it will remove those, its like ARGH !! to me without having internet connection, when i had internet connection everything worked fine.

---

