---
title: "Text editing in command line"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by dunomous on 2006-03-30
I realize that gedit and vim are ways to edit text files. I'd like to edit my mouse cursor, in doing so it is required of me (I believe) would be to edit a file recquiring root access. 

```

[Icon Theme]
Inherits=Human

```

obviosly needing to change the inherits value. Which (text editor) should I use to edit it?

---

### Post by xXx 0wn3d xXx on 2006-03-30
[QUOTE=dunomous]I realize that gedit and vim are ways to edit text files. I'd like to edit my mouse cursor, in doing so it is required of me (I believe) would be to edit a file recquiring root access. 

```

[Icon Theme]
Inherits=Human

```

obviosly needing to change the inherits value. Which (text editor) should I use to edit it?[/QUOTE]
Go under System>Preferences>Mouse

Then select your sursor theme. You may need to install more.

---

### Post by dunomous on 2006-03-30
Well that's why I'm at this editing in the Terminal. It does not recognize it in those settings. Only Human.

---

### Post by sn123 on 2006-03-30
[QUOTE=dunomous]Well that's why I'm at this editing in the Terminal. It does not recognize it in those settings. Only Human.[/QUOTE]
Install gcursor which would allow you to change cursor themes.
```

$ sudo apt-get install gcursor

```
Once the installation is complete, you can either run gcursor directly from terminal or run it via System menu-->Preferences-->Cursor selection

S

---

### Post by dunomous on 2006-03-30
alright, will the theme be recquired to be compiled before hand? When I try to install the theme, I don't know what file to tell it to install

---

### Post by xXx 0wn3d xXx on 2006-03-30
[QUOTE=dunomous]alright, will the theme be recquired to be compiled before hand? When I try to install the theme, I don't know what file to tell it to install[/QUOTE]
No, just download the theme then drag/select it from the window. (Gcursor)

---

### Post by IYY on 2006-03-30
If you want to edit a file from the command line (as root): sudo nano <filename>

---

### Post by dunomous on 2006-03-30
Yeah, that's what seems to be my problem. It's not allowing me to drag it, not being able to install. 

Ah, thank you IYY :D

---

### Post by sn123 on 2006-03-30
[QUOTE=dunomous]alright, will the theme be recquired to be compiled before hand? When I try to install the theme, I don't know what file to tell it to install[/QUOTE]
Find any cursor theme that you like & download it. Open gcursor and click on "Install Theme" and point it to the downloaded tar file.
For starts you can browse through [http://www.gnome-look.org/index.php?xcontentmode=36](http://www.gnome-look.org/index.php?xcontentmode=36) to see if there's something that you like :)

S

EDIT: to answer your question on text editor, you can use any editor that you're comfortable with to edit a file (to edit xorg.conf file you would need to use sudo).
$ sudo gedit /etc/X11/xorg.conf
OR
$ sudo nano etc/X11/xorg.conf

---

### Post by dunomous on 2006-03-30
Yes, that is where I got my cursor theme to install from. To be specific, Grounation-0.3.

Actually, it's a tar.bz2. Should I uncompress it and recompress it as a .tar file?

---

### Post by xXx 0wn3d xXx on 2006-03-30
[QUOTE=dunomous]Yes, that is where I got my cursor theme to install from. To be specific, Grounation-0.3.

Actually, it's a tar.bz2. Should I uncompress it and recompress it as a .tar file?[/QUOTE]
Try it and see if it works.

---

### Post by dunomous on 2006-03-30
no luck

---

### Post by sn123 on 2006-03-30
[QUOTE=dunomous]Yes, that is where I got my cursor theme to install from. To be specific, Grounation-0.3.

Actually, it's a tar.bz2. Should I uncompress it and recompress it as a .tar file?[/QUOTE]
As far as i remember it should work without having to compress and recompress as tar & unfortunately I am not on Ubuntu currently to verify it. Which flavor of Ubuntu are you using? Dapper seems to have issues with  getting custom x11 cursor themes to work.

---

### Post by dunomous on 2006-03-30
Not sure, I'm thinking Breezy.

---

### Post by sn123 on 2006-03-30
[QUOTE=dunomous]Not sure, I'm thinking Breezy.[/QUOTE]
Never mind I just logged into ubuntu and tried the theme and well it didn't work using gcursor. The reason I guess is that it's got more than one cursor themes (one for left-handed too). Anyway, so I installed it manually. Here are the steps:
Double click on the .bz2 file, it should show a folder called /Grounation-0.3/, double click and on Grounation-0.3, select Grounation and click on extract (I extracted it on the desktop). The folder called Grounation should be created on your desktop.
Now open a command terminal and create a new folder under .icons:
```

$ mkdir .icons/Grounation

```
copy/move the files from the desktop Grounation folder to .icons/Grounation
```

$ cp  Desktop/Grounation/*.* .icons/Grounation
$ cp  Desktop/Grounation/cursors .icons/Grounation/cursors

```
make sure that .icons/Grounation folder is created and has index.theme file and cursors folder within it.
```

$ ls .icons/Grounation

```
Open gcursor and choose Grounation as your cursor theme.

EDIT: easier way, is to copy the Grounation folder from your desktop to .icons folder using nautilus (file manager). Start nautlius and press CTRL-H to show hidden files and copy-paste your desktop Grounation folder under .icons 

HTH,
S

---

### Post by dunomous on 2006-03-30
should I do this as root (looking at your $ symbol). After trying to with just user access it does not work. When trying to copy it there, it just goes to the next line. No error message, but no copy either.

---

### Post by sn123 on 2006-03-30
[QUOTE=dunomous]should I do this as root (looking at your $ symbol). After trying to with just user access it does not work. When trying to copy it there, it just goes to the next line. No error message, but no copy either.[/QUOTE]

No you dont' have to do it as root (we are only modifying your user preferences). Try using the shorter method which is by using nautilus (Places Menu-->Home Folder), in nautilus press CTRL-H to view hidden files (or use View Menu-->Show Hidden Files). Copy the entire Grounation folder that you extracted into Home Folder/.icons
Open gcursor and scroll to the very end, you should see Grounation as an installed theme.
Also cp command doesn't show you "*n* files copied" message, so just make sure by using a ls command whether files were indeed copied or not in your previous post.
```

$ ls .icons/Grounation

```


S

---

### Post by dunomous on 2006-03-30
arg, sorry. I forgot to save my edit, It worked!

---

### Post by sn123 on 2006-03-30
[QUOTE=sn123]
```

$ cp  Desktop/Grounation/*.* .icons/Grounation
$ cp **-r** Desktop/Grounation/cursors .icons/Grounation/cursors

```
make sure that .icons/Grounation folder is created and has index.theme file and cursors folder within it.
```

$ ls .icons/Grounation

```
Sorry, I missed out a -r switch (for recursive) in my previous post. I would recommend using nautilus though as mentioned in my last post.

S

---

