---
title: "[SOLVED] can't unistall paltalk"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Harisz750 on 2008-02-28
i installed paltalk on ubuntu gutsu 7.10.. didn't work and now i want to unistall it. however , i can't!!!!  i tried through wine but it says: invalid unistall control file: c:/program files/paltalk messenger/irunin.xml       i also have xp installed on a seperate partition and unistalled paltalk from there as well cause i couldn't unistall it and thought it would be a good idea.. apparently not!!!!   any ideas anybody??? or i have to format ubuntu?????

---

### Post by Harisz750 on 2008-02-28
now i unistalled wine from synaptic.. but paltalk still remains there!!!!!!   i want to get rid of this please!!!!!

---

### Post by Oldsoldier2003 on 2008-02-28
> **Harisz750 said:**
> now i unistalled wine from synaptic.. but paltalk still remains there!!!!!!   i want to get rid of this please!!!!!

Uninstalling wine probably wasn't the best answer to purging the app. Your local wine programs can be found under  ~/.wine/drive_c/Program Files if the uninstaller in WINE doesn't remove the program you can delete the program's directory to rid yourself of the program. The reason you see the shortcut still is your uninstall of WINE wasn't complete, ```
apt-get purge wine
``` would heave removed your hidden .wine directory and all its contents thus removing the shortcut from your menus. 

For the best latest information on WINE you should go to [WINEHQ]("http://www.winehq.org/") or if you feel confident you can esit the wine registry files and remove references to the errant program.

---

### Post by Harisz750 on 2008-02-28
it didn't work... wine was unistalled.. paltalk still the same problems

---

### Post by Oldsoldier2003 on 2008-02-28
> **Harisz750 said:**
> it didn't work... wine was unistalled.. paltalk still the same problems

if wine was removed of course pal talk will have a problem since its a windows32 executable. you need to remove it from the wine directories on your computer (which are hidden )then remove it from the wine registry files, which are also hidden...

---

### Post by Harisz750 on 2008-02-28
how i find these directories and  wine registry files you talk about???  i have no idea... thanks for your help... i am new in ubuntu

---

### Post by Oldsoldier2003 on 2008-02-28
> **Harisz750 said:**
> how i find these directories and  wine registry files you talk about???  i have no idea... thanks for your help... i am new in ubuntu

```
cd ~/.wine
``` or CTRL +H in Nautilus will allow you to view hidden files and directories. Also look at this thread :
[http://ubuntuforums.org/showthread.php?t=649793](http://ubuntuforums.org/showthread.php?t=649793)
To explain how to get rid of the Icon in your menu's

Wine is not a perfect program yet so there are always a few little issues like this to deal wit. like i said before the WINEHQ website is a great source of information on WIne if you cant find the answer here.

---

### Post by Harisz750 on 2008-02-28
ok.. thanks. i found it out. and now i reinstalled wine without paltalk..   the only problem is that my camera is always on.. and don;t know if it has anything to do with that.. any way,, i will figure it out. thanks

---

