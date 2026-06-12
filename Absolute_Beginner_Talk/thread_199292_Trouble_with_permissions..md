---
title: "Trouble with permissions."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by neogia on 2006-06-18
So, how do I enable Ubuntu to install/create folders? For instance, I tried installing Adobe Acrobat Reader 7.0 and I just ran the install script and it failed because it didn't have permission to create a folder.

I know I can use a package installer, but I'm trying for a more general answer. If I just download a .tar.gz installer from anywhere, how do I give it the proper permissions to install?

---

### Post by Kilz on 2006-06-18
[QUOTE=neogia]So, how do I enable Ubuntu to install/create folders? For instance, I tried installing Adobe Acrobat Reader 7.0 and I just ran the install script and it failed because it didn't have permission to create a folder.

I know I can use a package installer, but I'm trying for a more general answer. If I just download a .tar.gz installer from anywhere, how do I give it the proper permissions to install?[/QUOTE]
In the case of installing software with a script run the script with sudo, it in effect is running it as the administrator. That way it will be able to create folders in non user areas. So if the script is foo.script and the instructions tell you to enter the command ./foo.script . Use 
sudo ./foo.script

---

### Post by neogia on 2006-06-18
Ok, but even more general then. Let's say I'm editing the x server configuration file. When I try to save my changes, it says I don't have the right permissions, but I'm the main account on the computer. How would I go about something like that?

---

### Post by Kilz on 2006-06-18
[QUOTE=neogia]Ok, but even more general then. Let's say I'm editing the x server configuration file. When I try to save my changes, it says I don't have the right permissions, but I'm the main account on the computer. How would I go about something like that?[/QUOTE]
you could use 
```
sudo gedit /path/to/file
```
or  if you want to have a gui to move around in, move files etc.
```
gksudo nautilus
```
will open the Nautilus file manager as an administrator, but be careful, what you do as sudo could ruin your system.

---

### Post by xXx 0wn3d xXx on 2006-06-18
[ Read this tutorial for more information on file permissions. ](wiki.ubuntu.com/FilePermissions)

---

### Post by pinellaschuck on 2006-06-18
[QUOTE=Kilz]you could use 
```
sudo gedit /path/to/file
```
or  if you want to have a gui to move around in, move files etc.
```
gksudo nautilus
```
will open the Nautilus file manager as an administrator, but be careful, what you do as sudo could ruin your system.[/QUOTE]

Just wanted to thank Kilz as the above post answered my question even before I had a chance to post it.
Respectfully
Pinellas Chuck
Florida USA

---

### Post by ZeusABJ on 2006-06-18
Hey Neogia, sorry to butt in on your post, but this thread hits really close to home on some issues I'm having too. So far all I'm hearing is people say is that you have to go to the Terminal window and create folders using the **sudo** command (if you are working outside your home folder or folders in which you don't have ownership). What I'd like to know is if there is a way to just use the GUI to create a folder. I mean I'd much rather right-click and choose "Create New Folder". Is this just not possible in Ubuntu? Can you not just click an icon and run your GUI in "sudo mode" (for lack of a better term)?

---

### Post by neogia on 2006-06-18
[QUOTE=Kilz]you could use 
```
sudo gedit /path/to/file
```
or  if you want to have a gui to move around in, move files etc.
```
gksudo nautilus
```
will open the Nautilus file manager as an administrator, but be careful, what you do as sudo could ruin your system.[/QUOTE]

[QUOTE=ZeusABJ]Hey Neogia, sorry to butt in on your post, but this thread hits really close to home on some issues I'm having too. So far all I'm hearing is people say is that you have to go to the Terminal window and create folders using the **sudo** command (if you are working outside your home folder or folders in which you don't have ownership). What I'd like to know is if there is a way to just use the GUI to create a folder. I mean I'd much rather right-click and choose "Create New Folder". Is this just not possible in Ubuntu? Can you not just click an icon and run your GUI in "sudo mode" (for lack of a better term)?[/QUOTE]

Just use
```

gksudo nautilus

```

---

### Post by ZeusABJ on 2006-06-19
[QUOTE=neogia]Just use
```

gksudo nautilus

```[/QUOTE]


SSSSSWWWEEEETTT!!! This was EXACTLY what I wanted. All I'm going to do is create and assign permissions to about 6 directories and this will do the trick perfectly! I doubt that will hose anything.

Thanks!

---

