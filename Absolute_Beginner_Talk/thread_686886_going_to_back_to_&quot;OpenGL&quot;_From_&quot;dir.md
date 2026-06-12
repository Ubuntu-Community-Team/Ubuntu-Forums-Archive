---
title: "going to back to &quot;OpenGL&quot; From &quot;direct3d&quot;"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-02-03
Hi everyone i was playin Condition Zero... and i wend and cheked the Direct3d box...and the screen got all messed up i cant switch it back... i tried everything uninstalling then installing the game again. 
Some one plz help me! thanks

---

### Post by Bluestick on 2008-02-03
bump*

---

### Post by Bluestick on 2008-02-03
OMG no one knows how to do this.... sad face :(

---

### Post by emarkd on 2008-02-03
Just a thought, but when you uninstall things the config files are usually left behind, so if you reinstalled it without removing them the old configuration is still in effect.  To remove the config files when you uninstall, do

```
sudo apt-get remove --purge $whatever
```

Maybe that'll work...

---

### Post by st33med on 2008-02-03
Direct3D is for Windows, isn't it? What are you using to play this game? WINE? Cedega?

---

### Post by spiderbatdad on 2008-02-03
```
sudo startx
```??? then reboot.

---

### Post by allquixotic on 2008-02-03
Hello there,

Condition Zero is a Windows game. I assume you are playing it through some sort of emulation. Are you running it through:

1. Wine?
2. Cedega?
3. Crossover Linux?

Your answer would determine the next step, but basically, the minimal fix would be to find the Condition Zero settings file (probably a .ini file) stored in the program directory, edit it and change the setting. If you don't know how to do that, a more general solution would be to delete

~/.wine (if you're running it through wine)
~/.cedega (if you're running it through cedega)
~/.crossover (if you're running it through Crossover Linux)

and then reinstall the game from the original media.

Before you delete **anything**, be sure to back up any files you can't afford losing: license keys, passwords, screenshots, savegames, etc. The entire Condition Zero game, and likely your installation of Steam, all reside in one of the three folders given above, if you've installed Condition Zero the proper way through an installer.

Of course, I really have no idea about your setup because you didn't give any details, so for all I know you could be running the executable off your Windows drive, and in that case, none of these instructions would apply.

By the way: 33 minutes from original post is **hardly** enough time to determine that "no one knows" how to solve your problem. Please show some semblance of patience.

Kind Regards,

Sean.

---

### Post by Bluestick on 2008-02-03
im using wine-doors! sorry about that im just really frustrated you know...

 k i have regular wine, but im running steam tru wine-dorrs!

---

### Post by emarkd on 2008-02-03
> **Bluestick said:**
> im using wine-doors!

Then my advice won't work ;)  Sorry.

---

### Post by Bluestick on 2008-02-03
> **emarkd said:**
> Then my advice won't work ;)  Sorry.
thats cool thx alot for trying i appreciate it!
 anyone else want to take a shot at this?
 everytime i open up condition zero, the screen  is all messed up making imposible for me to change it to OPENGL :(

---

### Post by st33med on 2008-02-03
Do you have compiz/compiz fusion running? If you do, turn it off and try again.

---

### Post by allquixotic on 2008-02-03
> **Bluestick said:**
> im using wine-doors! sorry about that im just really frustrated you know...

 k i have regular wine, but im running steam tru wine-dorrs!

Hi,

I am not familiar with wine-doors. Particularly, I am not sure how their "bottling" mechanism works. You might want to check [Wine-doors documentation](http://www.wine-doors.org/wordpress/?page_id=4) to see if they give any details about how to totally erase a particular application. You'll want to get rid of Steam and all Steam games, to be safe. Try to find the *path to the files in the filesystem* -- the uninstaller might not remove files that are touched after you install the game, one of which would be the configuration file. If you have the path to the files, you can simply delete the whole directory.

Good luck,

Sean.

---

### Post by Bluestick on 2008-02-03
> **st33med said:**
> Do you have compiz/compiz fusion running? If you do, turn it off and try again.
k i tried that, it didnt work :(

---

### Post by Bluestick on 2008-02-03
i have tried to uninstall it, but it said it could not find the uninstall file :(
 il just out of options here..

---

### Post by Lord Illidan on 2008-02-03
Are there any configuration files that the game uses? Perhaps you need to remove the entire .wine-doors directory and start over...or else try and find where the game is depositing the config file.

---

### Post by Bluestick on 2008-02-03
> **Lord Illidan said:**
> Are there any configuration files that the game uses? Perhaps you need to remove the entire .wine-doors directory and start over...or else try and find where the game is depositing the config file.
i was thinking about that too!! 
 how would i go about removing wine-doors? is a terminal command for that?

---

