---
title: "Huge problem with Ubuntu"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-24
:( 


 Question  Serious Problems with Ubuntu/Gnome
I have some serious problems with my ubuntu computer. Yesterday my computer was working perfectly and today all hell broke loose.

I have no idea what happened.


Here are some of my problems

1. Bug Buddy is in an endless loop. It will not stop. I press close every time and it just comes back. If I use system monitor to force stop it, it still comes back. If I tell it to save it will save, but it just comes back in an endless loop.

2. I have no access to any of my menus in gnome. I can see them but when I click on them they do not appear.

3. The computer did fsck several times but it has not helped.

Initially the kernel would not boot and I had to manually do fsck because the automatic fsck failed every time.


Wierdly enough I can click on some icons on my desktop but have no access to the gnome menus. I.E. I have no access to applications, places or systems.


4. Alt f2 does not work.


I would GREATLY appreciate any help you can give me to recover my computer.

Thanks


:(

---

### Post by apjone on 2007-02-24
try creating a new user and log in as them, if you still get the problem then it is a o/s problem , else it is sum thing with the users profile.

---

### Post by jprb85 on 2007-02-24
I have no access to the menus so I cannot create a new user.

---

### Post by robophred on 2007-02-24
Just did a quick check in the terminal.  Go to a different terminal (ctrl+alt+f1 to ctrl+alt+f8, f7 is  gnome, and f8 is the boot terminal it appears), and type 
useradd
You can get a list of the user commands by typing 'user', then double tapping the 'tab' key.
users-admin is the gnome user manager window, and probably wont work from the ctrl+alt+f# terminals (does anyone know the official name for those terminals?)

---

