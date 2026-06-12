---
title: "switch from ubuntu to xubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by windfer on 2007-02-27
is it possible to download xubuntu ontu ubuntu and delete ubuntu without having to use a live disc. ubuntu runs slow and xubuntu i am told runs faster so i would rather have xubuntu

---

### Post by muguwmp67 on 2007-02-27
You can use Synaptic to install the package 'xubuntu-desktop',  Then you will be able to choose from either Gnome or Xfce from the login screen.

After you do this you will be able to compare the environments, and you can later remove 'ubuntu-desktop' if you wish.

---

### Post by nrwilk on 2007-02-27
Or, you can just enter this in a terminal:
```
sudo aptitude install xubuntu-desktop
```

To remove gnome, and all the packages it installs that the xubuntu does not include, just issue this command:
```
sudo aptitude remove ubuntu-desktop
```

---

### Post by kittyhawk63 on 2007-02-27
> **muguwmp67 said:**
> You can use Synaptic to install the package 'xubuntu-desktop',  Then you will be able to choose from either Gnome or Xfce from the login screen.
After you do this you will be able to compare the environments, and you can later remove 'ubuntu-desktop' if you wish.

I just installed Xubuntu and logged out and was not given a choice at login between Ubuntu and Xubuntu. I rebooted and still was not given a choice. Any suggestions?
KH

---

### Post by freebird54 on 2007-02-28
I guess no one mentioned that there are a couple of ways to ge the choices.  On my (original) login screen, the bottom left corner lets you choose which session to start with - or hit F10 to have the menu pop up where you are.  Click the button next to your choice, the select change session, and answer whether or not you wish your choice to become the new default for nest time..

Hope this helps

---

### Post by kittyhawk63 on 2007-02-28
> **freebird54 said:**
> I guess no one mentioned that there are a couple of ways to ge the choices.  On my (original) login screen, the bottom left corner lets you choose which session to start with - or hit F10 to have the menu pop up where you are.  Click the button next to your choice, the select change session, and answer whether or not you wish your choice to become the new default for nest time..

Hope this helps

Yes, it does. Thanks freebird54. You get a gold star on your report card. :KS
kh

---

### Post by steven8 on 2007-02-28
> **freebird54 said:**
> I guess no one mentioned that there are a couple of ways to ge the choices.  On my (original) login screen, the bottom left corner lets you choose which session to start with - or hit F10 to have the menu pop up where you are.  Click the button next to your choice, the select change session, and answer whether or not you wish your choice to become the new default for nest time..

Hope this helps

I never mentioned it, because I didn't know it!  Thanks.  We learn something new every day!

---

### Post by kittyhawk63 on 2007-02-28
> **steven8 said:**
> I never mentioned it, because I didn't know it!  Thanks.  We learn something new every day!

Yes, we do Steven8. But you have been helpful on several occassions. Thanks again.
kh

---

### Post by steven8 on 2007-02-28
You are quite welcome.  I will still be seeking help in many areas as I go along, but I'll try to help out wherever I can.  :)

---

### Post by freebird54 on 2007-02-28
Gee - thanks for the Gold Star (TM).    It was certainly nice to see something I actually knew the answer to!  Amazing what playing with Beryl can give you...

---

### Post by kittyhawk63 on 2007-02-28
> **freebird54 said:**
> Gee - thanks for the Gold Star (TM).    It was certainly nice to see something I actually knew the answer to!  Amazing what playing with Beryl can give you...

Hitting the F10 does the trick. When I log out to change to xubuntu, the Options and Selections? at the lower left of the screen are inactivated for some reason. They only work for me when I first boot up. The F10 gets me what I need to make the selection.

Two additional gold stars for your report card. Two more and you can exchange them for a Big Mac. :mrgreen:   Not!

kh

---

