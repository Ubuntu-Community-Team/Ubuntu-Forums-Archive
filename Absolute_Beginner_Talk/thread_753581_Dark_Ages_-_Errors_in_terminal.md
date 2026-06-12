---
title: "Dark Ages - Errors in terminal"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Spoken on 2008-04-12
So, im trying to play one of my favorite games from the ol days when i used windows. its called Dark Ages, found at [Http://www.darkages.com](Http://www.darkages.com)

So, i download their client (the .exe file) and add it to the wine applications section in the wine configuration.

i then open terminal and drag the .exe file on my desktop to it. i move the cursor to the beggining of that line and add wine, so that it looks like this

wine '/home/spoken/Desktop/DarkAges719single.exe'

then i hit enter, and this pops up in terminal

fixme:spoolsv:serv_main (0 (nil))

then the installation wizard from windows pops up and installs the game, then when its done installing, i get this error in terminal

fixme:shell:IShellLinkA_fnGetPath (0x142098): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x142098): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\thidchk.dll") not found
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\Launch.dll") not found



WHAT DO I DO NOW???

:confused:

---

### Post by JoshuaRL on 2008-04-12
Try putting [this DLL](http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60) and [this DLL](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) into C:\windows\system32 and try installing again.

---

### Post by vgrisham on 2008-04-12
JoshuaRL is right; that should work. [This]("http://frankscorner.org/index.php") site also has some helpful ideas for getting games to work via wine.

---

### Post by JoshuaRL on 2008-04-12
You can also always check the [Wine Applications Database](http://appdb.winehq.org/) although it doesn't look like there's anything in there about it.

If you get it running right you could always submit it and be the maintainer for Wine.  That would be cool.

---

### Post by Spoken on 2008-04-13
.

---

