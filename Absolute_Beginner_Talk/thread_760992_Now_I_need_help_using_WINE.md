---
title: "Now I need help using WINE"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by yngvrr on 2008-04-20
I just installed Wine through the Terminl.. But now I cant find it.. What do I have to do? Im trying to install my pokerclient with it. However.. As I cant find and dont know what to do with it when and if I do find it I would be very happy to get instructions on what to do now.. 
can anyone help?

---

### Post by Tom--d on 2008-04-20
Just doubleclick the file .exe which is related to pokerclient. 

Wine then will start, (it loads the installer). Like when installing software in windows. 

To change the settings and all that. In terminal or a link type:
```
winecfg
``` 
Thats to change the settings
```
uninstaller
``` 
A GUI of uninstalling windows software on wine.

/home/your name/.wine/c_drive is where your C:/ is. (to look at hidden files, press CTRL + H once in home)

---

### Post by yngvrr on 2008-04-20
When I doubleclick the file.exe a textbox pops up that says : 

"Couldn't display "/home/ingvar/Desktop/PokerStarsInstall.exe"." 

when I write winegfc in the terminal something opens that looks like a Windows window. but I cant use all the options or look at all the layers(whatever its called) because it just closes..

As for the uninstaller.. Im trying to install so I dont know what to do with that..

What should I do now?

---

### Post by twright on 2008-04-20
click open with and select "wine windows emulator"

if it does not work try running it from the terminal with wine "path to installer" (if you just type wine in terminal then drag and drop the installer in that might be easier)

---

### Post by elmer_42 on 2008-04-20
This is a page specific to your application, I assume PokerStars, I have found [this]("http://appdb.winehq.org/appview.php?iVersionId=2899"). Supposedly it runs very well in Ubuntu.
But generally, I always use the terminal.
```
cd /path/to/file
wine program.exe
```
If that doesn't work, try this:
```
sudo wine program.exe
```
I am not a huge WINE maven, but I know that many other programs I have used require sudo. Try it without sudo first, then try it with sudo if it doesn't work. Good luck!

---

### Post by twright on 2008-04-21
might not be the best idea to run wine as root

---

