---
title: "Wine Directories"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by lillypilly on 2007-04-02
I have managed to get a Windows progame to run using wine. The only problem is the only way I can open that program is to go to winefile through the root terminal and then run the program.
On investigation I have discovered that when I use winconfg it is setting up two wine directories, one as "username/wine" and the other as "/root/wine". The program that I want to use then installs to the "root/wine" directory.
Is there some way that I can overcome this problem
Thanks

---

### Post by justleen on 2007-04-02
once wine is installed, you should run wincfg as user.

then install your application as a user (it will install in /home/user/.wine). that way you can run the programm as that user.

If you install the app as root, only root will be able to run it (it will install in /root/.wine)

---

### Post by zvacet on 2007-04-02
You can do it this way.Download exe in any folder but for now we will call it program.
```
wine /home/username/program/your_exe
```
This will start program and hopefully desktop icon.

---

### Post by lillypilly on 2007-04-02
Thanks, I can see the problem. I have been running wineconfg using an icon from the System Preferences menu. The only way I know how to start winefile is through the Root Terminal and I think that is what is causing the problem. Could you please tell me how to run winefile as a user and not Root Terminal
Thanks

---

### Post by justleen on 2007-04-02
erm.. on my system i can just right click an exe file, and it will have an option to launch in wine..

from a terminal:
Make sure you are a user, not root (issue the command whoami)
if it returns Root, you have a root terminal..
you can use ```
 su USERNAME 
``` to "logon" as a normal user
(of you start a terminal from Applications > terminal, you should not have root rights)

go the folder where the program is installed eg.  /home/user/.wine/drive_c/Prog files/Guildwars

then just start the exe with: ```
wine guildwars.exe
```

edit:
you can create a launcher on your desktop, offcourse
right click > add launcher
for the command, enter: wine  /home/user/.wine/drive_c/Prog files/Guildwars/Guildwars.exe
(change the Guildwars bit to your need ;) )

---

### Post by lillypilly on 2007-04-02
Well I have managed to get things installed in the right place.  su USERNAME done the trick. For some reason I do not seem to be able to get the program running without using "winefile" but I suspect it may be a couple of missing .dll files at the moment

Thanks for you help. Very much appreciated

---

### Post by justleen on 2007-04-02
> **lillypilly said:**
> ... For some reason I do not seem to be able to get the program running without using "winefile"...


Can you explain what you mean with "winefile" ?

Might be that we can help you a bit further again :)

I dont think your missing any files, otherwise  your not able to run it at all..

---

### Post by lillypilly on 2007-04-02
Yes, to get the program to run if I just go to the file using file browser when I right click on the file I get the option you mention above to open with wine. If I click on this nothing happens.
If I go through the Root Terminal and enter "winefile" it comes up with a window called winefile. This bring up a "explorer type" window and I can navigate to the file and then when I click on it it opens as I would expect and then I can use the program as I am used to within the "XP" enviroment. I read about going down this path somewhere during by browsing around the Net today while figuring out how to get "wine" running.
The normal method of right clicking on the item and using the wine option works on some other programs I have tried.
Thanks

---

### Post by zvacet on 2007-04-02
[http://www.securenet.net/members/jeanpelo/linux_guide.html]("http://www.securenet.net/members/jeanpelo/linux_guide.html")

Read LAUNCHING UTORRENT UNDER LINUX It explains how to crate launcher.

---

