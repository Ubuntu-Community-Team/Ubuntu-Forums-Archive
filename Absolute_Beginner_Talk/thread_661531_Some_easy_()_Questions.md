---
title: "Some easy (?) Questions"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Adbru on 2008-01-08
Hi Folks,

Spent a few happy hours trying to find my way round Fluxbuntu tonight.
Got a reasonable amount done but now have some VERY basic questions that I cant find the answer to (I have tried searching, honest !)

A high number of apps which I try installing from Synaptic do not appear in the start menu, sometimes a reboot is required but sometimes they have disappeared into the depths of the system. i.e. firefox.

If i enter "firefox" from a run command it starts up fine.

1/ how do I add a program to the start menu manually ?

2/ how do i add a shortcut onto the desktop for a program ?

next up will be installing the printer and setting up my wireless connection (once I get home from niteshift !! )

Thanks in advance, 

Adbru

---

### Post by peabody on 2008-01-08
My understanding is you have to add most of these things yourself when it comes to fluxbox.  I believe there's a fluxbox menu editor out there (heck, fluxbox's menu is just a text file if memory serves).

---

### Post by Adbru on 2008-01-08
By Heck this is a busy place !!

I go home for 12 hours and I'm on page 13  :)

Thanks for the info, I'll do some more digging.

Adbru

---

### Post by Walc on 2008-01-08
> **Adbru said:**
> By Heck this is a busy place !!

I go home for 12 hours and I'm on page 13  :)



that is what makes this place special right?:)

---

### Post by jseiser on 2008-01-08
This is from fluxbuntus webpage, might help with the menu.
---
Welcome to Fluxbuntu 7.10 Release Candidate!

Architectures: i386 (Built), AMD64 (Built), PowerPC (Pending Build)

There are a number of known issues for 7.10 RC

1. Ivman does not run (thus automounting appearing it does not work)

To fix this:

joejaxx@fluxbuntu:~$ mkdir ~/.ivman
joejaxx@fluxbuntu:~$ 

2. The Menu does not auto update after application installation

To fix this:

joejaxx@fluxbuntu:~$ sudo update-menus
Password:
joejaxx@fluxbuntu:~$

---

### Post by Adbru on 2008-01-08
Thanks guys,

The update-menus command helps sometimes....guess it depends on how the app was writen .

Another question (if i may) , how do i assosciate an application with a file type ??

i.e. I want OOwriter to auto open any word docs, it says to drag the app in but where from ?? or what is the name of the executable ??

May seem easy to you guys that know how but its driving me nuts !! 

cheers

Adbru

---

### Post by urukrama on 2008-01-09
For the menus, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=371144"). It should discuss everything you want to know about it, and possibly more :-)

I don't run Fluxbuntu, but I believe the icons on the desktop are controlled by idesk. To be sure, check if you have an .ideskrc (a hidden file) in your home directory. That is where all the idesk configuration takes place and where you add new icons. Have a look [here]("http://idesk.sourceforge.net/wiki/index.php/Idesk-usage").

---

