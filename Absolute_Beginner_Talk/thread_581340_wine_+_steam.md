---
title: "wine + steam"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-19
i just started with linux, and i really miss my half-life...  i found that if i use wine and steam i can install half-life.  i figured so far things have been awsome i couldnt go wrong but now im lost lol.  

i installed wine, i even got an auto update for it so im up to date now too.  a few problems though.  like when im installing steam all versions (with directions from this page : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)) i put in the first line of code it gives "wine iexplore http://winehq.org" and i get a window that pops up on the screen that i can not close, its always on top and nothing can be put on top of it, and it cannot be moved. (see screen shot)

[IMG]http://i213.photobucket.com/albums/cc307/kernel-fiesty/Screenshot-1.png[/IMG]

after that i reboot the computer because sadly thats the only way i know that closes that damn window, makes me miss alt+f4 from windows.  

i go back to the site and i pick up where i left off, i have the steam installer saved on my desktop and i terminal this next line "wine start SteamInstall.msi".  this is what i get in the terminal "fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found"

i really dont know what im doing wrong but then again i feel im toying with things way beyond me.  can anyone help me please?

---

### Post by shad0w_walker on 2007-10-19
1. Alt + F4 works just fine with Ubuntu. If it's not doing anything it sounds like the program has crashed.

2. Instead of the wine command try this

```
msiexec /i SteamInstall.msi
```

Edit: Forgot to mention

If your program has crashed you can force quit it by pressing Alt+F2 to open the run dialog and running this command:

```
xkill
```

You cursor should change to a cross, just click on the window you want to close and it will kill it. If you want to cancel xkill and not close anything any mouse click (Other than left) will do the trick.

---

### Post by LowSky on 2007-10-19
Step 3 shouldn't need to be done and is most likely why it is crashing your system, Steam should automatically installl gecko for you.

---

### Post by linux-loser on 2007-10-19
thanks for showing me how to close that annoying window, im sure ill see more like it.  

now i tried the command "msiexec /i SteamInstall.msi" and this is what i get "err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"SteamInstall.msi""

i also get a message after entering that command that states: "the specified installation package could not be opened.  Please check the file path and try again."

is it supposed to find it automaticaly on my desktop or am i supposed to add something to the begging of the "msiexec /i SteamInstall.msi" ?

sorry im just really new and still dont understand the filesystem entirely yet.

---

### Post by shad0w_walker on 2007-10-19
The command will assume that you in the same folder as the file. If the file is on your desktop try this instead.

```
msiexec /i ~/Desktop/SteamInstall.msi
```

---

### Post by Daveth on 2007-10-19
you may also find this useful....

[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

---

### Post by linux-loser on 2007-10-20
holy crap it works now thanks guys.

the "msiexec /i ~/Desktop/SteamInstall.msi" worked

---

