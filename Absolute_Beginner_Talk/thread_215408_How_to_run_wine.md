---
title: "How to run wine"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by goodfren on 2006-07-13
Hi Guys

How exactly I can run window program using wine?

What are the step i should do?

I have installed wine in the system but cannot it in application area, is it normal?

Thks

---

### Post by goodfren on 2006-07-13
I mean cannot find wine in the applications area.

---

### Post by Sonofmoog on 2006-07-13
Wine is transparent, and doesn't show up in the menu .. least, not in the GNOME menus .. Open a console and type

```
locate wine | grep bin
```

and you'll see a lot of files, most of which are shell scripts.  I haven't messed with wine in a good long while, so I'm not sure how to advise you where to begin.  Try winecfg and maybe winelauncher <path of Windows executable>

---

### Post by Billquinn1 on 2006-07-13
When you right click on an exe file the menu should give you the option to "open with wine windows emulator"
Have you followed one of the tutorials on setting up wine? (including running winetools)

---

### Post by goodfren on 2006-07-13
I get this after run wine

oem@ubuntu:~$ winelauncher/desktop/fourp1.exe
bash: winelauncher/desktop/fourp1.exe: No such file or directory
oem@ubuntu:~$ winelauncher fourp1.exe
Invoking /usr/bin/wine fourp1.exe ...
wine: could not load L"c:\\windows\\system32\\fourp1.exe": Module not found
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Wine failed with return code 126
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

Can this mean this window program is not suitable?

thks

---

### Post by goodfren on 2006-07-13
> **Billquinn1 said:**
> When you right click on an exe file the menu should give you the option to "open with wine windows emulator"
Have you followed one of the tutorials on setting up wine? (including running winetools)
I don see any open with wine window

That is why i ask about why i don see the wine in application, so that I can read the help file.

Can you guide me to check if my wine setup is correct.

thks

---

### Post by Billquinn1 on 2006-07-13
It looks like you are missing the font packs. This guy has a good tutorial on the whole wine setup process. It seems kind of lengthy but it works. The font installation is part of it. 

[http://doc.gwos.org/index.php/WineSetup](http://doc.gwos.org/index.php/WineSetup)

If you have already done all of this then it may be a program that wine does not like.

---

### Post by jimmygoon on 2006-07-13
(I think) He is executing the program improperly and thus Wine is not able to find said program and thus throws an unfortunatly hard to interpret error. (I'm guessing that based on this line: "wine: could not load L"**c:\\windows\\system32\\fourp1.exe**": Module not found"

What folder is this windows program in?

try the following:

"wine /path/to/the/program.exe"

and obviously replace those folders and the filename with the actual program information...

---

### Post by CarpKing on 2006-07-14
Before you do anything, just open up a terminal and type "wine --version"
this should tell you what version of wine you have installed.  If it fails to do so, wine is improperly installed.  Typing "wine --help" will give you a brief overview of how to use wine.

---

### Post by goodfren on 2006-07-14
Now i have success to extract the file but now I cannot find where my program is store, base on installation, it was in the c:\program files area, but i am not able to find where my C drive is place in my computer.

Pls advice

thks

---

### Post by trent dillman on 2006-07-14
Enable hidden folders in your file manager. The c drive is in a folder named .wine

---

### Post by goodfren on 2006-07-14
where is the file manager locate?

thks

---

### Post by trent dillman on 2006-07-14
Well, if you are in Gnome, you should be able to go to Places > Home Folder...that brings up Nautilus, the Gnome file manager.

---

### Post by goodfren on 2006-07-14
i am very sorry, i do not where is Gnome, could you please guide me by step?

Is in applications / Places or System?

thks

---

### Post by trent dillman on 2006-07-14
Gnome is the desktop environment. If you see Applications, Places, and System on your panel, you're in gnome. :-)

---

### Post by goodfren on 2006-07-14
ok, i find it, tq very much for your quidence

Thks

---

### Post by trent dillman on 2006-07-14
no problem :)

---

