---
title: "My gksudo has deserted me!"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Audunhb on 2006-05-19
Hi,

First of all, I'm a total noob. Installed hoary last week, and did my uppgrade to breezy today. Everything went perfect untill I installed Kalzium and Kstars for fun.

It seems to me that the installation got stuck, or at least the desktop environment started partially freezing up (no fonts) just after it. 
Anyhow.... I did my best MS move (reboot), which only resultet in ubuntu booting into a terminal window. Startx bugged, and I finally "fixed" it using my second MS move (reinstall): "sudo apt-get dist-upgrade". Startx still does not start during boot, but at least it does so when i give the command.

What worries me most now is that programs such as "Add Applications", "Synaptic Package Manager", and "Update Manager" all give me the same error message:

-->
**Cannot launch entry**
Details: Failed to execute child process "/usr/bin/gksudo" (No such file or directory)

gksudo is gone

sudo works though... and I can do whatever installation and upgrade I want from a terminal window.

Does anyone know how I could get my gksudo back?

---

### Post by macdo on 2006-05-19
It looks like you've moved to KDE on the desktop.
What happens when you press Alt+F2?
Do you have a button on that window called Options?
If so, click it, choose "run as a different user", user root, and your password.

---

### Post by bluevoodoo1 on 2006-05-19
Do you have the "gksu" package? I think that might it. There are a couple of libraries with it as well. libgksu1.2-1 and libgksuui1.0-1

```
sudo apt-get install gksu libgksu1.2-1 libgksuui1.0-1
```



You can also run synaptic, add applications and update manager with sudo. 

sudo synaptic
sudo gnome-app-install
sudo update-manager

You'll enter your password into the terminal instead of the nice little popup.

---

### Post by Audunhb on 2006-05-19
:)  Thanks!

I'm back home from work now, so I won't be able to test you'r excellent ideas before monday :-k 

But these fast replies really made smile :D

---

### Post by Audunhb on 2006-05-22
Macdo:
When I press Alt-F2 I get the "Run Application" window, but there's no properties button on it.

Bluevoodoo1:
The reinstall failed with error "Couldn't find package libgksu1.2-1", but it worked when I removed the libraries and did the install with only the gksu package
```
sudo apt-get install gksu
```
The installation went smoothly, adding this extra bit of information that I do not know if explaines why I got this problem:
"Selecting previously deselected package gksu"

Gksudo starts as before and everything seems perfect :D 

I honestly do not think I deselected any package while installing the educational software, but then again I keep mistrusting my colleagues when they swear they "didn't touch anything" :rolleyes: 

Thank you!

---

### Post by Sef on 2006-05-22
> I honestly do not think I deselected any package while installing the educational software, but then again I keep mistrusting my colleagues when they swear they "didn't touch anything

Set up the main account to be nonadministrative, and go into the administrative only when necessary.

---

