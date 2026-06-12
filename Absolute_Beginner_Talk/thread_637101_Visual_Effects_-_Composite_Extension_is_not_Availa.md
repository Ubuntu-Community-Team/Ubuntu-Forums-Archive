---
title: "Visual Effects - Composite Extension is not Available"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by linux4life88 on 2007-12-10
I've looked at other threads on this topic but I still can figure it out. I have an ATI Radeon Xpress 1150 128mb graphic's card. I've downloaded the driver xorg-driver-fglrx and it worked to enable my restricted graphics card but when I go to change the Visual Effects I still get the message:

Composite Extension is not Available

Why? And is there any way to fix it.

---

### Post by spiderbatdad on 2007-12-10
did you:
```
sudo apt-get install compizconfig-settings-manager xserver-xgl
```?

---

### Post by spiderbatdad on 2007-12-10
then reboot. after reboot go to Applications->System->Preferences->Appearance->Visual Effects...and choose Custom

---

### Post by linux4life88 on 2007-12-10
No I haven't. I've heard of the things that you mentioned but I don't really understand what installing these things will do.

---

### Post by spiderbatdad on 2007-12-10
the compizconfig-settings manager is necessary to activate and configure with composite windows manger. xserver-xgl is usually required with ATI cards. I'm not sure you should have changed drivers. just try:
```
sudo apt-get install compizconfig-settings-manager
```
then reboot to see if you get the effects working. remember to go to appearance and select custom

---

### Post by linux4life88 on 2007-12-10
I installed compizconfig-settings-manager and I clicked on custom and I still get the message:

Composite Extension is not Available

So should I unistall xorg-driver-fglrx and install xserver-xgl instead and see if that works?

---

### Post by spiderbatdad on 2007-12-10
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
is what you want, I believe. Then:
```
sudo apt-get install xserver-xgl
```

---

### Post by Ub1476 on 2007-12-10
Also post the output of

```
compiz
```

---

### Post by jamesey on 2007-12-10
This fixes this particular issue almost every time. I have a similar ATI card. 

First, run this in the terminal

```
sudo gedit /etc/X11/xorg.conf
```

Put 1 instead of 0 in the last section of xorg.conf so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection

---

### Post by linux4life88 on 2007-12-10
> **jamesey said:**
> This fixes this particular issue almost every time. I have a similar ATI card. 

First, run this in the terminal

```
sudo gedit /etc/X11/xorg.conf
```

Put 1 instead of 0 in the last section of xorg.conf so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection

I tried this and this is what I got:

Could not save file /ect/x11/xorg.conf
You do not have the permissions necessary to save the file.
Check that you typed the location correctly and try again.

How can I not have the permission to change a file? It is my computer and I'm the only user?

---

### Post by spiderbatdad on 2007-12-10
you must enter the command as the poster above showed..,."sudo"


Code:

sudo gedit /etc/X11/xorg.conf

make sure to enter the command as shown...notice X11, for example is case sensitive.

you had a small x11, and misspelled /etc.

Could not save file /ect/x11/xorg.conf
You do not have the permissions necessary to save the file.
Check that you typed the location correctly and try again.

---

### Post by jamesey on 2007-12-11
> **linux4life88 said:**
> I tried this and this is what I got:

Could not save file /ect/x11/xorg.conf
You do not have the permissions necessary to save the file.
Check that you typed the location correctly and try again.

How can I not have the permission to change a file? It is my computer and I'm the only user?

I'm a noob, but I found out you can paste into the terminal. This has saved me a lot of headaches. 
highlight this and copy it:

sudo gedit /etc/X11/xorg.conf

open the terminal. hit ctrl+shift+v

---

### Post by linux4life88 on 2007-12-11
I'm not sure what I did, but I got the file changed. Now it is giving this:

Desktop effects could not be enabled.

I'm starting to think this is going to be a lost cause, but oh well. Thanks for all the help everyone.

---

