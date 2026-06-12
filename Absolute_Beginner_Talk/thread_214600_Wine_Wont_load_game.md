---
title: "Wine Wont load game"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-07-12
Im trying to get wine to load my WINXP Game, however, it wont let me copy the game folder anywhere onto the Linux partition, it will only let me copy the folder to the desktop, no where else. And im presuming it wont run a game from a NTFS WinXP drive? Also, I need to get wine to understand that my game is in the desktop, not in C:// mainly as C:// isnt writable by Ubuntu.


May i also Point out how poor i think Ubuntu is. it is far too complex, what happened to one click Installs!

---

### Post by Captain Kirk76 on 2006-07-12
Bump

---

### Post by Qrk on 2006-07-12
Have you ensured that you have write permissions to the directory you are trying to copy to? Thats not really the problem here though.

I don't think you are understanding Wine at all. Wine is more like a guest operating system than a program. You need to install your game to Wine, in the virtual windows directory. You can't just copy and run any odd .exe and expect Wine to know what to do with it before you've installed it. Can Windows do that? 

You'll need to run a program to configure wine, use

```
winecfg
```

to help you set it up. You then need to make a little "virtual windows" install, with dependencies that your game might need.

Winetools, [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/) is great for installing your program's dependencies, like IE, installshield ect...

You probably won't have much luck finding help here without a more detailed description of your problem. Which game won't install? With which file manager are you trying to copy the files?

Lastly, Ubuntu is an excellent operating system. I assure you, if I did not absolutely love it, I would not be here, nor would many others. Please accept that we all volunteer here and be respectful.

---

### Post by Captain Kirk76 on 2006-07-12
Never mind, if i need to reconfigure Ubuntu/Wine for it to play a basic 1995 game (Transport Tycoon Deluxe) its the last straw, im going back to Windows

---

### Post by Kilz on 2006-07-12
> **Captain Kirk76 said:**
> Never mind, if i need to reconfigure Ubuntu/Wine for it to play a basic 1995 game (Transport Tycoon Deluxe) its the last straw, im going back to Windows
Can you just copy the files off the cd it came on to XP and have it work? Most games require you to install them in windows, thats the same thing here. Wine is a windows emulator, in other words it acts like windows. Just there is no "wine" gui program, it runs silently in the background.
Find the setup/install exe, right click on it, choose "open with other Application. The list of applications will open. At the bottom click on Use Custom Command, a space to type in will open, type in wine, then open. The setup program will run just like on windows.
You will only have to do this once, then wine will be assoicated with exe files, just double clicking on them and wine will open them.

---

### Post by Captain Kirk76 on 2006-07-12
Well i need to clear this up, Transport Tycoon Deluxe Patch (hereafter TTDPatch) Is a version of Tranport Tycoon deluxe, the orignal TTD is now abandonware, and a disk of it is rare, In Windows, there was a seperate program to install the registry files for it to work, however, wine wont even activate!

---

### Post by Captain Kirk76 on 2006-07-12
bump

---

### Post by Captain Kirk76 on 2006-07-12
bump

---

### Post by kigina on 2006-07-12
did you install it to your windows drive?

---

### Post by Qrk on 2006-07-12
You may want to check wine's hq for more information. I don't use wine at all.

However, winetools makes setting up wine an easy, GUI process. Once  you've installed the programs you need (install shield etc) it should resemble windows 98, and you may not need to edit your registry at all. Lastly, if you know what dll's you need, those you can copy from windows.

---

