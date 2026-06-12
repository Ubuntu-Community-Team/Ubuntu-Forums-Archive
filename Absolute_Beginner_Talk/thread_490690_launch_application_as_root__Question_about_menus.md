---
title: "launch application as root?  Question about menus"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Bubs on 2007-07-02
Is there a way to launch a application in the "Applications menu" as root? 

 I installed vmware server and it just about only works when I run it from sudo in the terminal.  if I'm not in sudo mode I can't create vm's and I can't run vm's that were created by root.

so I wanted the shortcut to be able to run in sudo mode.  like when you launch synatptic from the menus it asks for a password before use...  is there a way to do that with other apps?

thanks bubs

---

### Post by jcronkhite on 2007-07-02
I found this in the forums, does this help?
Original post is at [http://ubuntuforums.org/showthread.php?p=1402543]("http://ubuntuforums.org/showthread.php?p=1402543") by Matthew:


Right click on the desktop, select "Create Launcher..."

In the dialog box enter the following:

Code:

```
Name: Nautilus as Root (or whatever you want to call it)
Generic Name: anything you want
Comment: anything you want
Command: gksudo nautilus
Type: application
Icon: (click to select and pick one you like, maybe from /usr/share/pixmaps)
```

Hit "OK"

---

### Post by cwood06 on 2007-07-02
you can run applicatiosn by there name

such as 

gedit or text editor

sudo gedit 

it will launch a root version of the program if you are not sure what to use you can put it on the desktop and check the launcher for the command

---

### Post by Nekiruhs on 2007-07-02
> **cwood06 said:**
> you can run applicatiosn by there name

such as 

gedit or text editor

sudo gedit 

it will launch a root version of the program if you are not sure what to use you can put it on the desktop and check the launcher for the command
Sigh, please use gksudo instead of sudo for graphical apps. Sudo is designed for terminal apps only. To make a long story short, i got bit when I ran sudo gedit and somehow lost privelages to sudo. Meaning i had to go into recovery mode and fix it. Just play it safe, its only two more letters to type.

---

### Post by Bubs on 2007-07-04
sorry I found the problem it was a vmware issue I don't use it often...  I had to untic the "make private" button so I can run the vm's as another user.

also I was asking if there was a way to run the programs in the "applications" menu at the top (ie: Accesories, games, graphics ...) as root.

thanks for the help though

---

### Post by Nythain on 2007-07-04
edit thier menu entry (not sure how in gnome) and add gksudo in front of the command

---

