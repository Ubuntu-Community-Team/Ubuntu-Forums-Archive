---
title: "How do i delete a directory"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by treborblack on 2006-08-21
i'm using kubuntu the files in my home folder. The directory is called <mount point> and is owned by root.

Tried rm but it complains about a unexpected line break.

i'm utterly lost:confused: if i were using suse/mandriva i'd log into the gui  as root not clever at the best of times i know, but i could just click them with a mouse to get rid of them.

been on windows too long:roll:

---

### Post by taurus on 2006-08-21
```
sudo rm -rf <directory>
```

---

### Post by mithras86 on 2006-08-21
> **treborblack said:**
> i'm using kubuntu the files in my home folder. The directory is called <mount point> and is owned by root.

Tried rm but it complains about a unexpected line break.This will do the trick if the folder is empty:```
sudo rmdir path/to/dir
```And you can use this if your folder isn't empty:```
sudo rm -rf /path/to/folder
```> i'm utterly lost:confused: if i were using suse/mandriva i'd log into the gui  as root not clever at the best of times i know, but i could just click them with a mouse to get rid of them.

been on windows too long:roll:In Gnome you can create an extra item in your menu with ```
sudo gedit /usr/share/applications/Nautilus-root.desktop
```With the content:```
[Desktop Entry]
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;
```There should be something like that for KDE, but I don't know it. Just UTFS and you'll find out :p

---

### Post by treborblack on 2006-08-21
Thanks Taurus.

This is the result of the ls command 
roback@roback-desktop:~$ ls
alfa romeo                                                Examples
google-earth
Desktop                                                   <mount point>
roback@roback-desktop:~$

have tried typing in sudo rm -rf <mount point> and this is the result
roback@roback-desktop:~$ sudo rm -rf <mount point>
bash: syntax error near unexpected token `newline'
roback@roback-desktop:~$

---

### Post by mithras86 on 2006-08-21
what's the terminal output with 'ls -alh'? You could just type ```
ls -alh>>save
```and post the content of the file 'save'

---

### Post by taurus on 2006-08-21
> **treborblack said:**
> Thanks Taurus.

This is the result of the ls command 
roback@roback-desktop:~$ ls
alfa romeo                                                Examples
google-earth
Desktop                                                   <mount point>
roback@roback-desktop:~$

have tried typing in sudo rm -rf <mount point> and this is the result
roback@roback-desktop:~$ sudo rm -rf <mount point>
bash: syntax error near unexpected token `newline'
roback@roback-desktop:~$
You need to replace the <mount point> with the actual name!!!  What mount point or directory do you want to remove?  Assuming you want to remove "alfa romeo" then

```
rm -rf "alfa romeo" (if you are the owner of that directory...)
sudo rm -rf "alfa romeo" (if you are NOT the owner of that directory...)
```
Please do not run those two commands above if you don't intend to remove "alfa romeo."  They are just exemples so, okay...  ;)

---

### Post by shoot2kill on 2006-08-21
if he wanted a GUI version, using kubuntu.. why not use
```

kdesu konqueror

```
this would have given him the mouse click and delete function... or did i miss something.. ???

---

### Post by treborblack on 2006-08-21
[QUOTE=shoot2kill;1406356]if he wanted a GUI version, using kubuntu.. why not use
```

kdesu konqueror

```

this did the trick for me;) many thanks. as you can tell i'm new to this. but  i've now ditched windows all together so i'll be hanging around 

Thanks guys page printed will look into the other suggestions as i become more comfortable:)

---

### Post by shoot2kill on 2006-08-21
remember the kdesu konqueror command, it will help you a lot if/when u want to modify, create or delete files in root folder, using a GUI...

glad i could help

---

