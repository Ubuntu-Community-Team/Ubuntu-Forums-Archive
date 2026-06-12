---
title: "Wine and programs in gnome"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Vega on 2005-11-28
I installed this PC game called gunz. the installation destination was C:\Program Files in installer mode when I ran wine. When the installer finished the icon gunz.ink shows up but I can't execute it. How do I execute my program?

thank you in advance as usual.

---

### Post by aysiu on 2005-11-28
Something like ```
wine "z:\home\vega\.wine\drive_c\Program Files\Gunz\Gunz.exe"
``` You did install it to /home/vega/.wine, right?

---

### Post by Vega on 2005-11-28
[QUOTE=aysiu]Something like ```
wine "z:\home\vega\.wine\drive_c\Program Files\Gunz\Gunz.exe"
``` You did install it to /home/vega/.wine, right?[/QUOTE]

not really sure my name on this machine is class. It says:  wine: cannot find 'z:homeclass.winedrive_cProgram'

---

### Post by akiro.yamamoto on 2005-11-28
That .lnk file is a windows through back. It can be deleted.
The fastest way to get to your program is to Right click on the desktop and create a launcher.
Give it a name...choose any icon and then .....

In the command fields the info should look something like this:

wine "c:\Program Files\DVD Decrypter\DVDDecrypter.exe"

Of course it won't be DVDDecrypter :smile:
But you get the general idea! Once wine is properly configured you won't need to specify the absolute path. If your still having problems.. check your wine configuration with:
CODE:
winecfg
and ensure that the info is correct and the path to your windows programs makes sense...
You could also browse to that directory (In nautilus: View >> Show Hidden Files) go to your .wine directory and try to locate the program
BTW what version of wine are you using.......
I'm currently using the 0.91.deb version I got from WineHQ and that bad boy works like a dream.. :smile:
I hope this helps.....

---

### Post by Vega on 2005-11-29
well it works but when I run it, wine asks for to download mozilla's active x. I say ok to download it but then when it checks for updates on default I get a run time error.

---

### Post by droogthib on 2006-07-16
Hi, I'm having a similar problem when trying to run Gunz in wine.
When I try to open the gunzlauncher.exe I get this message on the terminal:

thiago@thiago-desktop:~$ wine ./.wine/c/Arquivos\ de\ programas/MAIET/Gunz/GunzLauncher.exe
fixme:shdocvw:WebBrowser_QueryInterface (0x7fd5a360)->({cf51ed10-62fe-11cf-bf86-00a0c9034836} 0x7fbad86c) interface not supported
fixme:shdocvw:WebBrowser_QueryInterface (0x7fd5a360)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x7fbad910) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x7fd5a360)->(0x7fbad8dc)
fixme:shdocvw:OleObject_Close (0x7fd5a360)->(1)
thiago@thiago-desktop:~$

I have installed wine by a HOW TO fund in this forum and I have used the winetools to configure it, without any errors. I did tryed to configure gunzlauncher.exe by winecfg to run as in a windows Xp, not windows 98, but none of the windows versions' emulations work.

If anyone have any idea, please, do help me!

Thanks.

---

