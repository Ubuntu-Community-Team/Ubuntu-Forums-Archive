---
title: "The File Format is Invalid / Themes"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by ubbu on 2006-10-31
Hi,

I can not install a single theme till the day one I had Ubuntu.
It always come up with this error

```
The File Format is Invalid 
```

I am installing it from System/Preferences/Themes and dragging the tar.gz package in it. I click to install, than it starts to process but at the end come up with this error message.

Any idea what is the problem about it ?
Thanks very much in advance

---

### Post by SongQi on 2006-10-31
Where are you getting the theme files from?  Are you sure the themes apply to your window manager (i.e.: Gnome themes for Gnome, KDE themes for KDE)?

---

### Post by SunnyRabbiera on 2006-10-31
Sometimes themes on Gnome look are source code versions and source code packages are mostly in tar.gz

---

### Post by ecosprog on 2006-11-01
Try extracting the themes. If these are desktop themes you may find that they contain all the various components in the .tar.gz file - including the separate .tar.gz files needed to install the themes. In short the files you need are all compressed in one file. 

Hope this makes sense. Anyway, it can't hurt trying to extract them and having a look in the resulting folder.

---

### Post by ubbu on 2006-11-01
THanks for the responds

> Where are you getting the theme files from? Are you sure the themes apply to your window manager (i.e.: Gnome themes for Gnome, KDE themes for KDE)?
I m getting them from gnome-look and using gnome desktop on the other hand I even try kde themes just to see what happenes, same error message with them too

> Sometimes themes on Gnome look are source code versions and source code packages are mostly in tar.gz

I think I have tried hundreds of themes but all came up with this error message

> Try extracting the themes. If these are desktop themes you may find that they contain all the various components in the .tar.gz file - including the separate .tar.gz files needed to install the themes. In short the files you need are all compressed in one file.

Hope this makes sense. Anyway, it can't hurt trying to extract them and having a look in the resulting folder.
I tried this also. I extract to a folder than choose Install Theme and browse to the specified folder, and same error again. 

Just can't get rid of it.
Might there be something wrong with my gnome ? But I haven't been experiencing any other problems with my Ubuntu

---

### Post by ubbu on 2006-11-01
I think I messed up

I tried to download kde desktop to try themes on KDE, I read somewhere that I could have both gnome and kde simply by selecting the session from the start up screen. So I downloaded, finished, but nothing appeared at the start up screen but just Gnome options. There were no error messages I had come up with during the KDE desktop install process

So I am logging on with GNOME as usual, the interface is ok but the thing is for example application Kooka and some other applications gave errors while starting them. I think I did something wrong ??

---

### Post by tylerjames on 2006-11-08
```
sudo apt-get install kubuntu-desktop
```

that should do it for you

---

