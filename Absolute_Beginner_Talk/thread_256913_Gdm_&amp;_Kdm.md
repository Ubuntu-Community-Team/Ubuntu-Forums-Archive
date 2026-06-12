---
title: "Gdm &amp; Kdm"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-09-13
I was wondering how to beable to start both kde and gnome on the same computer.  I have used CTRL + ALT + F1 and turned off gdm. and then I used the command /etc/init.d/kdm start and it tells me that i can't because its not default.  What would I have to do in order to be able to run Gnome and KDE.  Yes I installed all the needed files.

---

### Post by linear on 2006-09-13
I believe F10 at the gui login prompt will give you a choice and allow you to change the default.

---

### Post by JNowka on 2006-09-13
Thank you, it works perfectly.

---

### Post by pravuil on 2006-09-13
The next time you login just change the session to kde. There should be a button that you can choose from at the login screen. Don't worry about kdm or gdm. You can unistall kdm considering you are using gdm as the default desktop manager.

---

### Post by jordanmthomas on 2006-09-13
I know the problem is solved, but to run kdm, you would need to 
```
/etc/init.d/gdm stop
kdm

```

To change to kdm permanently (note that kdm and kde are not the same thing!) you would edit this file
```
sudo nano /etc/X11/default-display-manager
```
change it from
```
/usr/sbin/gdm
```
to
```
/usr/bin/kdm
```
Press <Ctrl><x>
y
<Enter>
<Enter>
The next time you reboot kdm will be started instead of gdm.

---

### Post by shak541 on 2008-03-19
thank you jordanmthomas for these instructions.... i managed to get gdm working but not fully.... when I start my computer I still have to go through a manual logon screen.... without a graphical login... then I have to run sudo gdm... then login like normal.... do you know how to fix this problem??
nvm figured it out. I simply ran:
sudo dpkg-reconfigure gdm

and it worked correctly :D

---

### Post by zvacet on 2008-03-19
Read [this.](http://www.psychocats.net/ubuntu/kde)

---

