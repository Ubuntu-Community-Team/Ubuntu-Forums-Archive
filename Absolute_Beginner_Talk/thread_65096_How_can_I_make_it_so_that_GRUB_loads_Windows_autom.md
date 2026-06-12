---
title: "How can I make it so that GRUB loads Windows automatically?"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by LinuxLove on 2005-09-13
Forgive me if another post was made similiar, but even through search I couldn't find anything.

Basicly, my family uses Windows. I've told them countless times how to select Windows XP from the dual booter, yet somehow they're still confuse. To make it more convient for them, how can I make it so that GRUB loads Windows automatically instead of Ubuntu (BTW I use Kubuntu/KDE)?

---

### Post by aysiu on 2005-09-13
sudo gedit /boot/grub/menu.lst
change default 0 to default 3 (or whatever entry Windows is minus one)

default 0 defaults to the first entry
default 1 defaults to the second entry
default 2 defaults to the third entry
and so on...

---

### Post by LinuxLove on 2005-09-13
> bash: gedit: command not found
> sudo: gedit: command not found

?

---

### Post by aysiu on 2005-09-13
Are you using Kubuntu or Ubuntu?

Sorry. I just read your original post. You're using Kubuntu. In that case:

*sudo kwrite /boot/grub/menu.lst*

---

### Post by LinuxLove on 2005-09-13
I tried editting menu.lst without the terminal, but when saving it refused much like this:

> 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0


When going to properties of the file, the ownership is under "root" and group is under "root."

---

### Post by aysiu on 2005-09-13
That's why you *sudo* kwrite /boot/grub/menu.lst.
*sudo* gives you the power of root.

---

### Post by LinuxLove on 2005-09-13
> root@COMPUTER-01:/home/jeremy # sudo kwrite /boot/grub/menu.lst
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0


Thats what I did.

---

### Post by manicka on 2005-09-13
[QUOTE=LinuxLove] sudo: gedit: command not found
?[/QUOTE]
 take the colons out

sudo gedit  /boot/grub/menu.lst

---

### Post by aysiu on 2005-09-13
[QUOTE=LinuxLove]Thats what I did.[/QUOTE] Weird. How about this?

```
sudo nano /boot/grub/menu.lst
```

---

### Post by LinuxLove on 2005-09-13
[QUOTE=manicka]take the colons out

sudo gedit  /boot/grub/menu.lst[/QUOTE]

>  root@COMPUTER-01:/home/jeremy # sudo kwrite /boot/grub/menu.lst
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0

Did this, and I'm on Kubuntu.

I'm not sure why I can't access the file. I always thought Linux assumed that the user knew what he/she was doing.

--------------
EDIT:
Okay, great! sudo nano /boot/grub/menu.lst worked, and I changed the 0 to 4..one problem though.. how do I save? Simply closing out didn't work.

---

### Post by aysiu on 2005-09-13
[QUOTE=LinuxLove]
I'm not sure why I can't access the file. I always thought Linux assumed that the user knew what he/she was doing.[/quote] I'm not sure, either. [This is a screenshot](http://i22.photobucket.com/albums/b337/psychocats/628fe2ec.png) of me typing the command on Kubuntu, and kwrite comes up.

---

### Post by aysiu on 2005-09-13
[QUOTE=LinuxLove]
Okay, great! sudo nano /boot/grub/menu.lst worked, and I changed the 0 to 4..one problem though.. how do I save? Simply closing out didn't work.[/QUOTE] Control-X. You'll be asked if you want to save changes--say "yes!"

---

### Post by LinuxLove on 2005-09-13
[QUOTE=aysiu]I'm not sure, either. [This is a screenshot](http://i22.photobucket.com/albums/b337/psychocats/628fe2ec.png) of me typing the command on Kubuntu, and kwrite comes up.[/QUOTE]

As is mine. If I could save the file off terminal, it should work.

---------
EDIT:
> ^G Get Help         M-D DOS Format      M-A Append          M-B Backup File
^T To Files         M-O Mac Format      M-P Prepend         ^C Cancel     

This popped up after Yes.

---

### Post by aysiu on 2005-09-13
[QUOTE=LinuxLove]
This popped up after Yes.[/QUOTE] You mean [this](http://i22.photobucket.com/albums/b337/psychocats/e195e169.png)? Just press enter. It should pop you back to the terminal, and your file should be saved.

---

### Post by LinuxLove on 2005-09-13
Okay. Thanks a lot for your help! I didn't expect such a fast answer to my problem. :D

---

### Post by aysiu on 2005-09-13
[QUOTE=LinuxLove]Okay. Thanks a lot for your help! I didn't expect such a fast answer to my problem. :D[/QUOTE] I'm glad it all worked out in the end. Really, though, you shouldn't have to use nano. Kwrite *should* work. I wonder what's wrong. Oh, well. You got done what you needed to get done, right?

---

