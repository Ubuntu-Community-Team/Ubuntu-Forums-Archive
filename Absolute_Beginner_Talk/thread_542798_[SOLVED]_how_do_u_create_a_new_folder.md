---
title: "[SOLVED] how do u create a new folder"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-04
i know you right click new folder 
BUT you can not click on new folder it is not an option

---

### Post by MenZa on 2007-09-04
Depends where you are. Do you have the right permissions? Else, use the "mkdir <foldername>" in the terminal.

---

### Post by cwood06 on 2007-09-04
if you can right click and create one then you can right click and open or any other menu, if this is not what you wanted could you please explain more

---

### Post by rsambuca on 2007-09-04
It won't let you create a folder if you do not have write permissions for the folder that you are currently in.

---

### Post by Tiger-Smith on 2007-09-04
Go to "Applications>Accessories>Terminal" then type "sudo nautilus", this will give you full write permissions to every folder.

---

### Post by rsambuca on 2007-09-04
> **Tiger-Smith said:**
> Go to "Applications>Accessories>Terminal" then type "sudo nautilus", this will give you full write permissions to every folder.

Actually, it should be 

gksudo nautilus

---

### Post by MenZa on 2007-09-04
> **Tiger-Smith said:**
> Go to "Applications>Accessories>Terminal" then type "sudo nautilus", this will give you full write permissions to every folder.

Maybe we should ensure he doesn't break his box now, eh? >_>

---

### Post by shortybookit on 2007-09-04
> **Tiger-Smith said:**
> Go to "Applications>Accessories>Terminal" then type "sudo nautilus", this will give you full write permissions to every folder.

did this and it worked but when i closed the terminal and tried to create a folder in the spot it just worked in the option was not there when i right clicked

is this something you have to do everytime?

---

### Post by LaRoza on 2007-09-04
> **shortybookit said:**
> did this and it worked but when i closed the terminal and tried to create a folder in the spot it just worked in the option was not there when i right clicked

is this something you have to do everytime?

You can use the "Run Command", option, no terminal open.

---

### Post by rsambuca on 2007-09-04
You will have to do this if you want to create folders inside of a parent folder for which you do not have the permission to write to as the current user.  What are you doing that requires you to create folders in this way?

---

### Post by Vadi on 2007-09-04
Usually, you want to only create folders in your /home directory. And for there you don't need any special permissions.

---

### Post by asmoore82 on 2007-09-04
> **shortybookit said:**
> did this and it worked but when i closed the terminal and tried to create a folder in the spot it just worked in the option was not there when i right clicked

is this something you have to do everytime?

could you tell us *what *directory you are trying to create *where*
so that we can tell you that you should do so only in your home folder?

---

### Post by shortybookit on 2007-09-04
i was tring to creat a folder in file system but i guess i should only creat in home/eric

which i can but if this is the folder i would save all my stuff to i want a short cut on the desktop i can not click drag to desktop or right click copy 

how do i get it to the desk top

---

### Post by Tiger-Smith on 2007-09-04
To be honest it dosent really mater whether sudo or gksudo is used as there both the same thing just different purposes, gksudo is designed to be run from the gui I believe.

---

### Post by Vadi on 2007-09-04
Right click on the folder, and click 'create link'. Then you can just drag that link from nautilus onto your desktop, and voila.

---

### Post by asmoore82 on 2007-09-04
> **shortybookit said:**
> i was tring to creat a folder in file system but i guess i should only creat in home/eric

which i can but if this is the folder i would save all my stuff to i want a short cut on the desktop i can not click drag to desktop or right click copy 

how do i get it to the desk top

**middle-click** (or mouse-wheel-click) and drag it to the desktop.

EDIT: Oh!!!! my bad ... 

by default Ubuntu starts with the clean desktop look ...
to change this, open a terminal and run the command ...
```
~$ gconf-editor /apps/nautilus/desktop
```

and check-off the icons you want to see.

:KS

---

### Post by Tiger-Smith on 2007-09-04
Open a new terminal and type sudo nautilus /home/usernamehere/Desktop then create the folders wherever, *wonders why you need to do this* should already have write permissions to your own desktop.

---

### Post by Tiger-Smith on 2007-09-04
Ctrl+Shift then drag whatever you want shortcutting to the desktop.

---

### Post by Steveway on 2007-09-04
Don't use sudo nautilus.
It can fsck up your permissions.
Use gksu for graphical applications. (gksudo is just a symlink to gksu so they are the same but sudo and gksu are different commands.)

---

### Post by shortybookit on 2007-09-04
tiger smith i can save files to my desktop! that was not the question was it??? my q was how do i make a shortcut of my home dir on my desktop who wants a million files on my desktop i want a folder on my desktop OF HOME that i would make folders in side of this one

---

### Post by rsambuca on 2007-09-04
> **Tiger-Smith said:**
> To be honest it dosent really mater whether sudo or gksudo is used as there both the same thing just different purposes, gksudo is designed to be run from the gui I believe.

Sorry, but this is incorrect.  Applications run in X should not be run as root, as it can cause permission errors, and in some cases cause tremendous problems to your system.  Most of the time it doesn't matter which you use, but this is by chance.  As a safe computing practice, you should always start any program which opens a graphical user interface with gksudo, if it is required.

---

### Post by asmoore82 on 2007-09-04
Real Solution:

> **asmoore82 said:**
> 
EDIT: Oh!!!! my bad ... 

by default Ubuntu starts with the clean desktop look ...
to change this, open a terminal and run the command ...
```
~$ gconf-editor /apps/nautilus/desktop
```

and check-off the icons you want to see.

:KS

---

