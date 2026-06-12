---
title: "Mouse troubles"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by proudmonkeynum1 on 2006-04-15
Hi, im pretty new to linux and I need some help. I'm using an old MSoft 5 button serial mouse and it moved very slow. I found a way to fix that by going into the xorg.conf file and changing /dev/input/mice to /dev/ttyS0 and I did that. Now my mouse doesnt work at all. I tried to change it back, but when i open sudo nano /etc/X11/xorg.conf its blank. Any ways to solve this problem are much appreciated.

---

### Post by Bloch on 2006-04-15
Hi;
There should be a back-up copy of your xorg.conf file. It is called xorg.conf_backup
You might also have a backup like this one:
 /var/backups/xorg/xorg.conf.2006-01-12-20:33:14

Now put the back-up in the directory
/etc/X11
and rename it to xorg.conf

Then you can begin your experiments again!
(Or you can try  
sudo dpkg-reconfigure xserver-org
for a semi-automated configuration of xorg.conf)

---

### Post by dcstar on 2006-04-15
[QUOTE=proudmonkeynum1]Hi, im pretty new to linux and I need some help. I'm using an old MSoft 5 button serial mouse and it moved very slow. I found a way to fix that by going into the xorg.conf file and changing /dev/input/mice to /dev/ttyS0 and I did that. Now my mouse doesnt work at all. I tried to change it back, but when i open sudo nano /etc/X11/xorg.conf its blank. Any ways to solve this problem are much appreciated.[/QUOTE]
```
cd /etc/X11
ls *conf*
```
If you find the one you want to edit, then use nano, otherwise you may be able to rename the current one to something else, and rename the backup to the working file name.

---

### Post by proudmonkeynum1 on 2006-04-15
[QUOTE=Bloch]

Now put the back-up in the directory
/etc/X11
and rename it to xorg.conf

[/QUOTE]
How do I move it if my mouse doesnt work?

---

### Post by macdo on 2006-04-15
Did you back up your xorg.conf file? Try 
```
ls -l /etc/X11
``` 
and see if there's a file there called xorg.conf~ or anything with xorg.conf in the name (xorg.conf.old, ~xorg.conf, etc). If so, you might just be in luck!
Open that file with nano and see if it *is *a backup. If it is, do this (we'll call the found file xorg.conf~):
```
cd /etc/X11
``` 
(just saves a bit of typing by putting you into the X11 directory...)
```
sudo cp xorg.conf xorg.conf_wrong
``` 
(That will copy the non-working xorg.conf to a new file called xorg.conf_wrong, so that you can have a look at it later...)
```
sudo cp xorg.conf~ xorg.conf
``` 
(That replaces the non-working xorg.conf with the back-up)
And you should be good to go!

---

### Post by proudmonkeynum1 on 2006-04-15
Thanks I got it to work again, but it's still slow and moves jerky. I'm thinking of buying a Msoft wireless notebook mouse. Do you have any idea if that will help?

---

### Post by macdo on 2006-04-15
Should do. 
I've got a Logitech Cordless Click!, if that's any help.

edit: I didn't read the question properly... 
I have no idea whether a different mouse would help. I do have two suggestions:
1. Borrow a friend's mouse to see.
2. Make sure your (presumably ball) mouse isn't all crudded up round the ball. (Don't laugh, I actually called out a tech person once because of crud round the ball... That was some years ago, but I'm still embarrassed:))

---

### Post by proudmonkeynum1 on 2006-04-15
Yea it's a ball mouse, but I'm pretty sure it isn't cruddied up because it works normally in Windows 98. I'll see if I can borrow a friend's mouse.

---

### Post by proudmonkeynum1 on 2006-04-19
A few days ago i got a Microsoft wireless notebook mouse 3000 and it works like a charm. Thanks for you guys' help

---

