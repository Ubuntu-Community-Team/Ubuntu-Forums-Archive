---
title: "Window manager problem"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-04-13
hi all

i installed icewm but it slow me laptop down. so i uninstalled in using: 'sudo aptitude remove icewm'. now the windows are screwy and keyboard stop working. how do i go back to the default manager? and why did my keyboard stop working?

thanx,
Nolander.

---

### Post by slimdog360 on 2007-04-13
Are you asking how to reinstall gnome?

---

### Post by Nolander on 2007-04-13
no. i think its called x windows or something. i was running icewm with gnome but gnome isnt doin its job.

---

### Post by slimdog360 on 2007-04-13
well ```
sudo apt-get install xserver-xorg
``` should reinstall it.

But that seems a bit drastic, if I had to guess the following should solve it. Take a look in your /home/nolander (or whatever) folder, click on view then show hidden files. Look in there for a file called .Xsession or .initxrc (or something like this), it may even have icewm in the name (I cant be sure without looking at your computer. Cut this file out of there, and paste it anywhere but back in that folder, maybe on the desktop or something. Then restart X back into gnome.

edit: oh and if everything is back up and running fine just delete the file that you copied to the desktop or where ever

---

