---
title: "Permissions Issue when using GUI apps"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Jim Rogers on 2007-02-02
When using the GUI, i.e. printer setup, or  Places "explorer", I run up against permissions errors. I have to open terminal and use the command line "sudo <command>". Am I mssing something here?

---

### Post by geokok1981 on 2007-02-02
> **Jim Rogers said:**
> When using the GUI, i.e. printer setup, or  Places "explorer", I run up against permissions errors. I have to open terminal and use the command line "sudo <command>". Am I mssing something here?


You have rights to modify all the files in your "Home" directory.
When you are outside your "home", i.e. in /etc or wherever else in the filesystem, you need root privilages in order to modify files and folders. 
This is for your own security. As you said you can access these files using the "sudo" command which gives you root privillages. Make sure you dont delete anything by mistake though ;)

---

### Post by TwistesdTexan on 2007-02-02
Do you have administrator rights? <System> <Administration> <Users & Groups> HiLite your user name, then <Properties> Use the <User Privaleges> tab at thtop of the new box. Make sure administer the system is selected.

---

### Post by psyne on 2007-02-02
Also as point of reference whenever you are launching gui apps as a sudo make sure you use gksudo.

why?

[http://www.ubuntuforums.org/showthread.php?t=181867](http://www.ubuntuforums.org/showthread.php?t=181867)

Have the problems you mentioned been ongoing or have they started with this session and if so did you try restarting.

---

