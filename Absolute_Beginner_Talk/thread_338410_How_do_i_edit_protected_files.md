---
title: "How do i edit protected files"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Sir_Sid on 2007-01-14
I need to edit menu.lst in the grub folder. So i navigated over there via the gui interface because I cant seem to get CD to go to any of the root folders. The file is write protected though. How do I go about un protecting it so I can edit it.

---

### Post by taurus on 2007-01-14
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by ewankho on 2007-01-14
You can change the file's permission but I think it would be better if you edit the file as root instead of changing the permissions.

---

### Post by Sir_Sid on 2007-01-14
how do I even navigate there using cd? Or do you have to use gksudo

---

### Post by taurus on 2007-01-14
If you want to edit /boot/grub/menu.lst, you can use "gksudo gedit" or you can use the terminal text editor, "nano -w"!  It's your choice.

---

### Post by usien on 2007-01-14
4 future reference nautilus can be run in root mode by typing this in the terminal:
sudo nautilus
then u can modify files by opening from nautilus

---

### Post by houstonbofh on 2007-01-14
> **Sir_Sid said:**
> how do I even navigate there using cd? Or do you have to use gksudo
Some simple CLI commands.  You will need to open the terminal as described above.
```
cd /
```
Go to the root directory.
```
pwd
```
This is short for "print working directory" and shows you where you are.
```
cd /etc
```
Change directory up to root, then down into etc.
```
sudo nano filename
```
Edit filename as root with the cli editor nano.
```
gksu gedit filename
```
Edit filename as root with the graphical editor, gedit.
```
gksu nautilus
```
Open up a root file manager.  **This can be dangerous!**

---

### Post by steve.horsley on 2007-01-14
As others have suggested, the file is protected from modification by normal users. Rather than change the system setup by changing hte file permissions (which can do untold damage with some files), you should temporarily run an editor with root's identity instead of your own. Launching an application with sudo, gksu or gksudo launches them as root. GUI apps should not be launched by sudo - it can cause odd problems. These launchers generally ask for you (not roots) password before launching.

Doing things this way maintains the security of the system in that the files are never vulnerable to unauthorised modification by other users (or indeed other processes running in your name). There IS a point to this, even on systems with only one user, and that is safety from trojans and viruses etc. For instance, a trojan arriving in an email attachment could not modify the system files if you accidentally opened/ran it.

---

### Post by aysiu on 2007-01-14
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

