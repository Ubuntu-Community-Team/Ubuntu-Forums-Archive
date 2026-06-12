---
title: "How do you Run a program in Wine"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by joshgtv6 on 2006-10-22
Ok, this has to be the most newb question on the planet.  I downloaded a program called Highgrow that I used to run on windows.  It's a simulated marijuana growing program. LOL, don't ask.  I got wine to install it, and this is as far as i can get in the terminal.  

[email]jpeifley@jpeifley-desktop:~/.wine[/email]/drive_c/Program Files/HighGrow$ dir
BigLeaf.dat   Harvest.dat   HighGrow.mid  Mellow.mid   Skunky.mid
Boyous.mid    HighGrow.exe  INSTALL.LOG   Robbie.dll   Suzy.mid
Comments.dll  HighGrow.hlp  Legal.mid     Sensual.mid  UnGrow.exe
[email]jpeifley@jpeifley-desktop:~/.wine[/email]/drive_c/Program Files/HighGrow$


now in windows your would just type: HighGrow.exe or HighGrow to run the program.  What do I do in Ubuntu?  I don't know the command to get the game to start.  

Second question:  Where can I find these directories in the GUI interface that is built into Ubuntu?  

Sorry if this has been covered but damned if I could find it.  Thanks ahead of time.

---

### Post by divague on 2006-10-22
run it like this
$ wine HighGrow.exe

---

### Post by jordanmthomas on 2006-10-22
to run it in wine, once you're in that directory (like you are above)
type
```
wine HighGrow.exe
```

These directories are right where they say they are in the terminal.
The . in .wine means it is a hidden directory, so you have two options to get there in nautilus (file browser)
Hit Ctrl-L and type
[code]~/.wine[code]
or hit Ctrl-H to show hidden files.

**beaten

---

### Post by joshgtv6 on 2006-10-22
> **jordanmthomas said:**
> to run it in wine, once you're in that directory (like you are above)
type
```
wine HighGrow.exe
```

These directories are right where they say they are in the terminal.
The . in .wine means it is a hidden directory, so you have two options to get there in nautilus (file browser)
Hit Ctrl-L and type
[code]~/.wine[code]
or hit Ctrl-H to show hidden files.

**beaten

ok, that got me a bit further, now I have another issue.  

jpeifley@jpeifley-desktop:~/.wine/drive_c/Program Files$ wine HighGrow.exe
wine: could not load L"c:\\windows\\system32\\HighGrow.exe": Module not found
jpeifley@jpeifley-desktop:~/.wine/drive_c/Program Files$


I appreciate the help, i'm oblivious the terminal commands and navigating it.  I'm still awaiting a response in another thread about a good resource for terminal commands and how to use them.


EDIT: ok, i got it to startup through nautilus but it just locks up so i'm assuming that means that wine won't be able to run it.  I figured it was such a simple basic program that it would work.  Guess not.  Oh well, guess i won't be growing any cyber plants. LOL

---

### Post by jordanmthomas on 2006-10-22
```
wine "C:/Program Files/HighGrow/HighGrow.exe"
```
You were actually in the wrong directory and still needed to go into the HighGrow folder in Program Files
This command should run it no matter where you are.

---

### Post by ReaderRat on 2006-10-22
Terminal Commands - The Shell Game
                           - Alphabetical
         **[http://www.ss64.com/bash/](http://www.ss64.com/bash/)**
                  - Alphabetical - Search
         **[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)**
                  - Common Admin
         **[http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)**

---

### Post by joshgtv6 on 2006-10-22
> **jordanmthomas said:**
> ```
wine "C:/Program Files/HighGrow/HighGrow.exe"
```
You were actually in the wrong directory and still needed to go into the HighGrow folder in Program Files
This command should run it no matter where you are.

ok, i got it to startup both ways but the game just locks up once it starts so i'll assume that I need further tweaking for it to work or maybe wine just can't run this particular game.  But the crash course in hidden files and directories was much appreciated, that really helps more than you know.

---

### Post by joshgtv6 on 2006-10-22
> **ReaderRat said:**
> Terminal Commands - The Shell Game
                           - Alphabetical
         **[http://www.ss64.com/bash/](http://www.ss64.com/bash/)**
                  - Alphabetical - Search
         **[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)**
                  - Common Admin
         **[http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)**

thank you, thank you, thank you.  I've been looking for pages like these for days.  Damn i love this forum.  You all rock. :mrgreen:

---

### Post by x64Jimbo on 2006-10-22
> **joshgtv6 said:**
> ok, i got it to startup both ways but the game just locks up once it starts so i'll assume that I need further tweaking for it to work or maybe wine just can't run this particular game.  But the crash course in hidden files and directories was much appreciated, that really helps more than you know.
If you run winecfg, you can change what version of Windows it pretends to be. I've found that many games run better if I make wine pretend to be win98.

---

### Post by joshgtv6 on 2006-10-22
> **x64Jimbo said:**
> If you run winecfg, you can change what version of Windows it pretends to be. I've found that many games run better if I make wine pretend to be win98.

mega thanks.  I didnt' realize you could do that.  I saw that it was emulating in Windows 2000.  This program definetaly won't work like that.  So i tried it in XP and BAM!  I'm off setting up my growroom and the program works 100%.

---

### Post by brucewagner on 2008-01-07
Ok.....   I'm a newbie too...    But I figured this out.....  Hope it helps someone...

To INSTALL a Windows program to run under Wine:

I inserted my Quicken 2003 CD-ROM into the drive....  The Nautilus file manager opens...

I double-clicked on the Autorun folder...

I right-clicked on the AUTORUN.EXE file....  and selected "Open With Wine Emulator"....

The installation went exactly as if it were on Windows...  And it even added the launch shortcuts to the Wine's Programs menus...

And, most importantly, Quicken runs Perfectly!

(That was just for fun though, I'm migrating over to GNUcash to replace Quicken... :) )

---

