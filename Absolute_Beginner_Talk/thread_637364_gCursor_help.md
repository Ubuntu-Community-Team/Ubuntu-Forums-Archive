---
title: "gCursor help"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by PinkFloyd102489 on 2007-12-10
This has probably been asked before but Im not seeing any that detail my problem


Im running Compiz on Ubuntu 7.10. Im trying to install a cursor theme and I saw that gCursor was the way to go. I installed it, tried to install the theme with it, doesnt work. I tried dragging and dropping the tarball into Appearance, doesnt work either.


What do I do to install this pointer theme?

---

### Post by Vadi on 2007-12-10
I don't know, never tried, but I'll try and help. Could you give a link to the theme?

---

### Post by PinkFloyd102489 on 2007-12-10
[http://gnome-look.org/content/download.php?content=67833&id=2&tan=7289319](http://gnome-look.org/content/download.php?content=67833&id=2&tan=7289319)

---

### Post by Vadi on 2007-12-10
You need to get gcursor at first ([click]("apt:gcursor"), or type "sudo apt-get install gcursor" in the terminal). After that, alt+f2, type "gcursor", click on "Install Theme"...

... the button doesn't seem to work for me. Hm.

---

### Post by PinkFloyd102489 on 2007-12-10
Yeah I installed gcursor and it doesnt work. Known bug too.

I extracted the theme to my ~/.icons/ folder and it shows up in the Pointer preferences under Appearance, but I cant select it.

---

### Post by Vadi on 2007-12-10
Oh, that way worked for me. I just clicked on the thing, and it automatically changed. I extracted the whole aero-drop folder to ~/.icons

Edit: oh this looks pretty spiffy. The pointer thing. -off to find more pointers-

---

### Post by PinkFloyd102489 on 2007-12-10
That doesnt help me. -_-

I still cant get mine to change. Im using Compiz with Emerald.


EDIT: Wouldnt you know it, it changed right after I posted. *rolls eyes*

---

### Post by yabbadabbadont on 2007-12-10
If you like, I can provide instructions for installing the cursor theme globally.  It will take a bit of working in a terminal window though.

Edit: Well, looks like you got it to work while I was typing my reply.  :D

---

### Post by PinkFloyd102489 on 2007-12-10
Actually, it's being tempermental.


Cursor appears correctly in Thunderbird, shows Default in Firefox, and my white-glass everywhere else.


Halp?

---

### Post by yabbadabbadont on 2007-12-10
Logout.  Hit Control-Alt-Backspace to kill X and make it restart.  If that doesn't help, I can walk you through installing the cursor theme so that it is the system default and not just your default.

---

### Post by PinkFloyd102489 on 2007-12-10
Restarting the X server was the last thing from my mind, lol.


Completely fixed now, thanks.

---

### Post by Vadi on 2007-12-11
yabbadabbadont, could you still post the instructions on making it the system default? KDE apps aren't respecting my new cursor and are changing it back to the default whenever the mouse goes over them :(

---

### Post by yabbadabbadont on 2007-12-11
Open a terminal window.  Become root since we will need root permissions for every step.  :D
```
sudo -i
```
Now extract your cursor theme into the /usr/share/icons directory.  I am using Pinux's pUbuntu-24 cursors, so I will use them as an example.  Here is what my /usr/share/icons directory looks like after I extracted the cursors there.
```
/home/daffy $ ls -l /usr/share/icons
total 80
drwxr-xr-x  7 root root 4096 2007-12-09 03:24 Crux
drwxr-xr-x  2 root root 4096 2007-12-09 03:24 HighContrastInverse
drwxr-xr-x 11 root root 4096 2007-12-09 03:23 Human
drwxr-xr-x  7 root root 4096 2007-12-09 03:24 Mist
drwxr-xr-x  8 root root 4096 2007-12-09 03:27 Tangerine
drwxr-xr-x  7 root root 4096 2007-12-09 03:27 Tango
-rw-r--r--  1 root root  627 2007-04-20 11:26 application-default-icon.png
drwxr-xr-x  8 root root 4096 2007-12-09 16:57 crystalsvg
drwxr-xr-x  2 root root 4096 2007-12-09 03:23 default
lrwxrwxrwx  1 root root   10 2007-12-09 16:56 default.kde -> crystalsvg
drwxr-xr-x  9 root root 4096 2007-12-09 04:34 gnome
drwxr-xr-x  3 root root 4096 2007-12-09 03:22 handhelds
drwxr-xr-x 14 root root 4096 2007-12-09 18:58 hicolor
drwxr-xr-x  4 root root 4096 2007-12-09 04:34 locolor
drwxr-xr-x  3 root root 4096 2007-12-09 15:07 pUbuntu-24
drwxr-xr-x  3 root root 4096 2007-12-09 03:22 redglass
-rw-r--r--  1 root root 4351 2006-11-29 03:52 sun-java6.png
-rw-r--r--  1 root root 4779 2007-04-03 10:50 sun-java6.xpm
drwxr-xr-x  3 root root 4096 2007-12-09 03:22 whiteglass
lrwxrwxrwx  1 root root   19 2007-12-09 16:57 xine.xpm -> ../pixmaps/xine.xpm
/home/daffy $ ls -l /usr/share/icons/pUbuntu-24
total 8
drwxr-xr-x 2 root root 4096 2007-12-09 15:07 cursors
-rw-r--r-- 1 root root   74 2007-12-09 15:07 index.theme

```
Now we need to add our new cursor theme to the list of installed alternatives in /etc/alternatives.  First, we need to create a new theme file for our cursor theme.  This file is different than the index.theme file that is included with the cursor theme.  The new theme file will be located in /etc/X11/cursors.  I just copy one of the existing files to a new name and then modify the copy.
```
cd /etc/X11/cursors
cp core.theme pUbuntu-24.theme

```
As far as I know, you don't have to name it the same as the cursor theme, but giving it some other name might lead to confusion.  Here are the contents of the core.theme file.
```
/etc/X11/cursors $ cat core.theme 
[Icon Theme]
Inherits=core

```
And here is the pUbuntu-24.theme after I edited it for my new theme.
```
/etc/X11/cursors $ cat pUbuntu-24.theme 
[Icon Theme]
Inherits=pUbuntu-24

```
Now that we have our new theme file, we need to add it to the list of alternatives for "x-cursor-theme".  We do this using the update-alternatives command.  The syntax is confusing the first time that you use it, so you might want to read it's man page.  I messed up my cursors a few times before I figured out the correct order of the parameters.  :oops:  Fortunately (for you), I will provide the correct command here.  ;)
```
cd /etc/alternatives
update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/pUbuntu-24.theme 20

```
Now that we have added our new cursor theme to the list of installed themes, we need to set it to be the default one used by Xorg.
```
update-alternatives --config x-cursor-theme

```
Just select your new theme from the list that is presented.  Now exit out of the terminal and logout.  Hit Control-Alt-Backspace to force Xorg to restart.  Your new cursor theme should be used at this point.

---

### Post by Vadi on 2007-12-11
That's a lot of work. I got like 20 new cursors :(

Thank you for the nice instructions though, I'll do it this evening

---

### Post by yabbadabbadont on 2007-12-11
Just curious, why do you want to install 20 different cursor themes?  Or are you assuming that you have to follow these instructions for each individual type of cursor within one theme?

---

### Post by Vadi on 2007-12-11
20 different cursor themes (I found a pack of them!).

---

### Post by yabbadabbadont on 2007-12-11
In that case, just do each step for all 20 before proceeding to the next step.  That way you can use the up arrow to pull up the last command in your bash history and just change the name.

---

