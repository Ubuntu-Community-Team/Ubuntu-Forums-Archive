---
title: "How to open console"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Matt27272 on 2006-12-13
I know this may sound stupid, but I just got Ubuntu and I'm wondering how to open the console.

Also, I think I installed wine properly but cannot find the directory that its in.

---

### Post by meng on 2006-12-13
Open terminal: Applications > Accessories > Terminal

What do you mean by the directory that wine is in. Do you mean where is the executable located, or where is the virtual C drive?

---

### Post by Afoot on 2006-12-13
You open the console by going to Applications -> Accessories -> Terminal.

Wine is (or the things you install with it, rather) installed in a folder called ".wine" in your home folder (a dot before a name means that it's hidden). To access it, either just cd to it using a terminal, or press [CTRL]-[H] to see hidden files in nautilus (file browser) and go there.

---

### Post by Matt27272 on 2006-12-13
Ok I got that working, but now while updating steam, it stops at 26%.  Does anyone know how to fix this?

---

### Post by meng on 2006-12-13
Commonly reported problem, I don't know how to fix it.

---

### Post by Afoot on 2006-12-14
> **Matt27272 said:**
> Ok I got that working, but now while updating steam, it stops at 26%.  Does anyone know how to fix this?
I will quote the solution from winehq.com:
> 26% Bug Workaround:

Run this from the directory you installed Steam.

wine steamTmp.exe SelfUpdate "Steam.exe" 14


---

### Post by Matt27272 on 2006-12-14
Ok, how do I find out what the directory is that I installed steam?  What do I do to run wine steamTmp.exe SelfUpdate "Steam.exe" 14?

---

### Post by Afoot on 2006-12-15
> **Matt27272 said:**
> Ok, how do I find out what the directory is that I installed steam?  What do I do to run wine steamTmp.exe SelfUpdate "Steam.exe" 14?
It's located in wine's 'fake C:\ drive", which is located in your home folder, actually. It lies in "/home/yourusername/.wine/" (a dot before a folder/file name means it is hidden).

To get there, you can either use the console (Applications->Accessories->Terminal), or use Nautilus (the file browser). 

[SIZE="5"]Console Method[/SIZE]
To go to the directory using the console, type (assuming that you're in your home directory, which you are by default if you open a console as Your user. But if you aren't sure, type in "pwd" in the console):
```
cd .wine/drive_c/
```
... and you should be in your fake Windows drive.

From there, just cd to whatever directory you want, and type "ls" to see what's in the current directory, and "pwd" to check the path to the directory. Once you get where you want to be, you can use that command:
```
wine steamTmp.exe SelfUpdate "Steam.exe" 14
```

If you want to start wine from that directory, type:
```
wine Steam.exe
```

[SIZE="5"]Nautilus Method (file browser) NOTE: can't execute commands from here[/SIZE]
When you are browsing your home directory, type the following command to see hidden files (the ones starting with a dot), and then just browse your way to the file you want to start, then right click, open with, and type in "wine". And it should start.

It should be noted, however, that it is preferred that you 'are' in the directory of the thing you execute with wine. In other words, it's better to "cd" to the directory and execute it. You can do this each time if you want,  but you can make a simple script by making a file named "whatever.sh" and typing in the actual commands you would've run if in a console.

For instance, this ".sh" file would run World of Warcraft:
```
cd /home/fredrik/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
wine WoW.exe

```

And to run that ".sh" file, type, in the console:
```
sh whatever.sh
```

Good luck!

---

