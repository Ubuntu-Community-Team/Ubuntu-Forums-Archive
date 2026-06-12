---
title: "Non Existant Graphic Display"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by opensourcerocks on 2006-02-25
I just finished installing the default Kubuntu 5.10 install. Once it finishs loading,
I am prestented with no graphical screen. I am very new to linux and have no idea what to do? It just asks for my user name and password, then presents a place to enter commands(like dos.) I would like to fix this to see KDE when I turn on the computer, instead of some text command thing, that I have no idea what to do with.

Help Please?
Thanks

---

### Post by Xian on 2006-02-25
Verify that KDM is installed...

$ sudo apt-get install kdm

---

### Post by opensourcerocks on 2006-02-25
Thanks for the reply but still no luck in what you have suggested

---

### Post by aysiu on 2006-02-25
What was the error?

Try these commands--one at a time. If one works, you don't need to try the next. ```
startx
``` (start the graphical display) ```
sudo /etc/init.d/kdm restart
``` (restart the login screen) ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` (make sure you have all the packages you need) ```
sudo dpkg-reconfigure xserver-xorg
``` (adjust your video card settings).

---

### Post by opensourcerocks on 2006-02-25
There is no error just a place for me to type stuff in.
Also I am using 64 bit edtion of Kubuntu.

Thank You
I will try your suggestions and report back

---

### Post by opensourcerocks on 2006-02-25
Still no luck.
All of the commands execpt startx work properly.
When I use startx I gives me errors and un understable things.
Could it be my graphics card, or should I try Drapper?
Thanks

---

### Post by Xian on 2006-02-25
If you tried everything mentioned then your install is botched. Compare the md5sum with your ISO to make sure the data is not corrupted. Once you get that sorted then do the install again and look for any warnings or errors that appear during the process.

Also, it would be good to review the [Install Guide](http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/).

What is your gfx card?

---

### Post by opensourcerocks on 2006-02-25
Thanks for the reply
I have checked the iso md5 and they match
Although could it be because of a CD-RW
instead of a CD-R?

Also I have a ATI Shappier X700 if that helps

---

