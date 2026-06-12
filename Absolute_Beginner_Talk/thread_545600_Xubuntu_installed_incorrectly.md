---
title: "Xubuntu installed incorrectly"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-09-07
Hi, 
   I just installed Xubuntu and I believe something is wrong, here are some things I have noticed:
-No splash screen
-No audio
-Odd taskbar layout (see image)
-Gnome is still being used
-Grub shows that it is still Ubuntu
-The login screen is Xubuntu, but after logging in, the background goes orange and loads Ubuntu (with Ubuntu logo's and all...you can also see that in the screen shot)
-No Xubuntu themes or wallpapers (doesn't bother me...just seems like a result of an issue.)
-And the same amount of RAM that Ubuntu uses is still being used (I thought Xubuntu used less)

Am I missing something, or is Xubuntu supposed to run and look like this (if so...its odd to be running gnome and have Ubuntu logos)? I have reinstalled Xubuntu from the package manager twice now with the same results. I upgraded to Xubuntu from Ubuntu in the package manager with these packages: xubuntu-artwork, xubuntu-artwork-usplash, xubuntu-default-settings, xubuntu-desktop, xubuntu-docs, and xubuntu-system-tools. Any information about what went wrong and how I could fix it would help me and my friend who's computer I am working on, thanks a lot!

---

### Post by BrendanM on 2007-09-07
The Grub screen isn't going to change. At the login screen, go to "Session" and see if there's an option for "Xfce" (the Xubuntu window manager). If not, you should go to a terminal and do "sudo apt-get install xubuntu-desktop" and see what that gets you.

---

### Post by RomeReactor on 2007-09-07
Hi. A the login screen, press the **Options** button and then **Select Session**, and choose Xubuntu (or XFCE).

---

### Post by diatribe on 2007-09-07
I believe it is called xfce-session

---

### Post by kevindubrow on 2007-09-07
Ok I selected the right session, much better. Now just a few more questions:
-What can I do to fix the audio?
-Why is there no splash screen?
-And why is there still a high amount of RAM being used? I thought that Xubuntu could run on RAM as low as 64MB but it is using 178.4MB right now.

Thanks very much!

---

### Post by diatribe on 2007-09-07
you can select the spalsh screen through xfce preferences, does your audio work at all or just no login sound, and do you have anby other apps open that might be using ram?  also, do you load the gnome libraries on startup?  this will affect ram usage

---

### Post by kevindubrow on 2007-09-07
I just put in a CD, there is audio...apparently there is just no login or log out sounds. And how do I know if I am loading the gnome libraries? Thanks a lot!

---

