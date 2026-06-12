---
title: "After logging in, I get a brown screen"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by n00buntu on 2006-02-04
Hello,  I am new to Linux, and I'm stuck.  I installed Ubuntu just fine, but when I go to log in, I enter my username and password, then the screen goes brown and a few seconds later, a garbled Ubuntu logo appears, and nothing else happens.  When I tried to install Kubuntu, I don't even get a chance to log in.  Kubuntu results in a grey screen.  The mouse still works, but I can't do anything else.  I've tried several CDs/DVDs and all have the same result.  During the login screen, I can reboot and shutdown without problem.  

I am very excited to try Linux, but I'm stuck at the starting point.  Any advice is greatly appreciated!

---

### Post by AndyCooll on 2006-02-04
Seems that the X-Server (the software that handles your graphics hasn't configured properly

Press CTRL+ALT+F2, this should give you another terminal (F1-F6 are command line, F7 is usually the default GUI, i.e. the one that is currently stuck). Login and and make a backup copy of the file you are going to re-configure: 
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then type the following:
```
sudo dpkg-reconfigure xserver-xorg
```

You will now be taken through a process of re-configuring your graphics set-up again. For most you can accept the defaults. You might want to change the graphic card to "vesa" which is a basic graphics card set-up (IIRC) .

When you've finished and it's dropped you back in to the command line again, type:

```
startx
```

If it doesn't work you can always retry the process. Post your results.

:cool:

---

### Post by n00buntu on 2006-02-04
I was not able to copy the file, but I followed the rest of your instructions.  I switched to vesa, and disabled the auto-monitor check.  Voila, I am now the newest Linux user!  I am writing this post from my new Linux machine!  Thank you so much.  You have ended 5 days of torture trying to figure this out!

---

### Post by AndyCooll on 2006-02-04
That's because my copy instructions should have had "sudo" at the beginning as below (my apologies):

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Anyway, happy to help and welcome to the wonderful world of Linux!

:cool:

---

### Post by n00buntu on 2006-02-04
I am happily working on Ubuntu thanks to you.  I had heard that linux users were very helpful and friendly.  Now I know that is true.  Thanks again.

---

