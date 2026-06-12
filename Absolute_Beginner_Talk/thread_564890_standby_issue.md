---
title: "standby issue"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by zementente on 2007-10-01
hi,

i tried to find an answer in other posts, but if there was anything, i simply didnt get it - i'm new to ubuntu (or linux in general).

My system goes into standby after a while, even though standby should be turned off - in power managment as well as in my bios (i think). Once it has, it won`t come back up.
Mouse and keyboard seem to be dead. If i press the reboot button, my screen stays dark. I have to turn the computer off completely.

is there any solution?

p.s. i am using feisty fawn

---

### Post by sirgogo on 2007-10-02
Hey:

I was having the same issue a while back. One of the things you might want to check is whether or not your graphics drivers are installed, and whether it will support the screen-saver or other features.

In my case, my nvidia restricted drivers weren't installed, causing this to happen. This phenomenon caused my computer to freeze and for me to crash it manually. However, I did fix this by installing the restricted drivers.

Later on, I accidentally messed up and screwed up my nvidia drivers (search google for nvidia board/graphics drivers ubuntu). As a result, my screen saver would try to activate, turn the screen black, and thus force me to crash my computer. However I fixed this problem by using some generic drivers.

Addressing your problem of not turning off your screen saver, I'm sure you have gone through System ---> Preferences ---> Screen Saver, but just making sure ;). One thing that you might want to try is editing your xorg file (filesystem --> etc --> X11 --> xorg.conf), which you might have to log in as root to do.

I'm not really sure what else may have gone wrong based on your description, so let me know how it goes. Good luck!

---

### Post by shaoming1980@gmail.com on 2007-10-02
:guitar:Sirgogo, awesome!  my problem has been totally resolved! It is my Restricted Driver for ATI Xpress 200 video card that caused that,  thanks , Sirgogo!  :)

---

