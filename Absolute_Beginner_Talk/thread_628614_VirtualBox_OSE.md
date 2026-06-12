---
title: "VirtualBox OSE"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-01
I have a simple problem, i dont really need virtualbox i just wanted to install xp so that i could write simple vbs and bat viruses (lol). 

This thing is completely out of my leage but i just would like to experiment with it

1. Do i have to have my own cd copy of xp ? or will it lnstall its own virtual windows ?

2. I am reciving this error when installing it. 

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by annda on 2007-12-01
hi,

to answer your questions:

1. yes, you do need an actual windows install cd - and not one of those oem "recovery" cds most people have nowadays.

2. just go to system>administration>users and groups>manage groups and select your username in vboxusers' properties.

---

### Post by XVII on 2007-12-01
Why are you going to be writing viruses anyway?

---

### Post by psychobeauty on 2007-12-01
hi u can also download and install vmplayer...download the win32 image for vmplayer and you dont need a cd

---

### Post by Taras on 2007-12-02
Thanks guys it was helpful

---

### Post by darkazurka on 2008-06-27
Thanks, I went to System->Control Centre->(typed "user" and selected "User and groups" and did what you said annda especially on the 2nd, now it works, and doesn't complain.

---

