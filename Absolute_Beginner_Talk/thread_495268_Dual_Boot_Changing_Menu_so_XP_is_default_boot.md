---
title: "Dual Boot Changing Menu so XP is default boot"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by guntercb on 2007-07-07
Hello,

I have successfully downloaded Ubuntu and have created a duel boot on my computer!  Ubuntu  seems to rock!  When boot up my computer if I do not do anything it automatically loads Ubuntu.  Considering my wife uses this machine and is not familiar with Ubuntu, but wants XP this is not good.  Can someone help me so that I can change it so that by default the computer will boot to XP.  

Right now when I boot up I get a menu with choice one is Ubuntu and choice four is XP.  If you don't make a selection in like 9 seconds the computer just choses what is highlighted (choice one Ubuntu).   Is there some way I can change choice one to be XP so if we don't respond in the correct amount of time it just loads XP instead of Ubuntu.

Thank a million.  Hope to get everything up and running and get wife hooked then I will just get rid of XP.

Cheers,
Chris

---

### Post by Happy_Man on 2007-07-07
Sure. Just edit /boot/grub/menu.lst with the command ```
gksudo gedit /boot/grub/menu.lst
``` and change the order of the entries down at the bottom so that XP is first.

---

### Post by Wiebelhaus on 2007-07-07
> **Happy_Man said:**
> Sure. Just edit /boot/grub/menu.lst with the command ```
gksudo gedit /boot/grub/menu.lst
``` and change the order of the entries down at the bottom so that XP is first.


easier to change the default number at the top to the xp installation...

[IMG]http://www.imagehosting.com/out.php/i876252_Screenshotmenu.lstReadOnlybootgrubgedit.png[/IMG][/URL]


see under warning it says default with a zero , count the "titles" at the bottom of the config file and enter the xp number there , like it's prolly #4

---

### Post by guntercb on 2007-07-09
Thanks for the replies.  They helped alot.  My wife now can boot directly to XP and I get to play with Ubuntu.  Now I have lots to learn.  

Cheers,
Chris

---

### Post by joe_doufu on 2007-09-07
After changing the configuration file, is it necessary to re-install the boot loader?  What's the command to do that?

---

### Post by rsambuca on 2007-09-07
Once you have made the changes to the menu.lst and saved them, it will be read by the grub loader on next boot-up.

---

### Post by joe_doufu on 2007-09-08
Can't save the modified file!  That irks me, I'm used to the Windows paradigm where if I give myself administrator access, I can edit anything.  I guess I need to log in as root.  How do I do that? ... can't do it from the main user login screen.

---

### Post by schorsch on 2007-09-08
```
gksudo gedit /boot/grub/menu.lst
```
This way you have root permissions to alter the file.

---

### Post by CowzRule on 2007-09-08
> **joe_doufu said:**
> Can't save the modified file!  That irks me, I'm used to the Windows paradigm where if I give myself administrator access, I can edit anything.  I guess I need to log in as root.  How do I do that? ... can't do it from the main user login screen.

Edit the file by opening the terminal and type```
gksudo gedit /boot/grub/menu.lst
```That will open the file for editing with root privileges and allow you to save it.

---

### Post by mrgooding on 2008-04-21
Note that the terminal is located Applications then terminal (took me a few minutes to find this when I first tried this!

---

