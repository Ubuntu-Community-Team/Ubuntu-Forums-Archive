---
title: "no permission to make folders or files -please help-"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by bubi1980 on 2006-09-03
hi,

I would like to create a skin folder for BMP. What I do is: open file system/usr/include/bmp/ and try to create a skin folder but dont have the permission to make or change folders files.
I have the same problem in "file system/usr/share/backgrounds (to change wallpapers).
I have a password and username, am I not the root?
please help me out

---

### Post by Klaidas on 2006-09-03
Try doing it as root - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

In short, just > sudo mkdir directory_name

---

### Post by whizbaby on 2006-09-03
The root account is not set active by default (and don't turn it on for fun, have good reasons). You (as the one who installed the system I suppose) have the ability to gain root privileges for a short time by using one of the commands 'sudo' or 'gksudo' (e.g. in terminal **sudo** *command*).
What you're trying to do is storing data where you are not meant to be as a normal user. The only reason to store data somewhere else as in your home is to make it accessible system-wide (for all users on the computer). Unless it's that what you want put your data in your home.
(if you still want to do it:
save-file-in-home
open-terminal
      **sudo cp *filename destination***

or for graphical interface with root privilege, let's say thunar:
       **sudo thunar**)

---

### Post by bubi1980 on 2006-09-03
thx

---

