---
title: "Azureus can't update because /opt/.azureus/ isn't writable, and WINE problem"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Frostshock on 2006-08-19
I installed Azureus through Automatix, and it's getting annoying enough that I might switch to Bittornado or use uTorrent on Windows (unless uTorrent can run on WINE) if I can't solve this.

Also, when I type wine c:\\Program Files\\World of Warcraft\\WoW.exe -opengl I get an error saying Wine can't find c:\Program, like it doesn't continue past the space in Program Files. It's Wine 0.9.19, compiled from source code since it needs a patch to run WoW on nVidia cards right. I deleted the patch file from the wine top directory after running the patch -p0 thing before compiling it, would that cause a problem?

---

### Post by kepos on 2006-08-19
don't you need to type '\' before eache space in path of file?

---

### Post by TFX360 on 2006-08-19
c:\\Program Files\\World of Warcraft\\WoW.exe -opengl

In windows < 2000 you needed to use

c:\\Progra~1\\World of Warcraft\\WoW.exe -opengl

Could you try that?

---

### Post by TFX360 on 2006-08-19
Kepos, that could be it too! Didn't think of that!

---

### Post by bodhi.zazen on 2006-08-19
Azureus is funky, it took me a while to figure out.

What you have is a permisssions problem.

Solution:
```

sudo chmod 777 /opt/.azureus/
```

you may not need to sudo.

Also utorrent runs fine in wine. 

[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)

---

### Post by Frostshock on 2006-08-19
*wine: cannot find 'c:\Progra~1\World'*

And I set it to XP.

---

### Post by kepos on 2006-08-19
wine c:\\Program\ Files\\World\ of\ Warcraft\\WoW.exe -opengl

have you tried that?

---

### Post by bodhi.zazen on 2006-08-19
When you installed wine, where did you put your "fake" c drive?

I put mine in ~/.wine/c

You also have too many and the wrong type of "\\". Linux uses /.
the \ is used because of the <space> in the path name.

Thus "Program Files" becomes "Program\ Files"

Also use the full path to WoW.exe starting with /home/.....

```

wine /home/username/path_to_c_drive/Program\ Files\World\ of\ Warcraft\WoW.exe -opengl
```

For me I would type:
```
wine /home/user_name/.wine/c/Program\ Files\World\ of\ Warcraft\WoW.exe -opengl
```

---

### Post by Frostshock on 2006-08-19
Sorry for the huge delay, I had a big internet connection problem.

wine c:\\Program\ Files\\World\ of\ Warcraft\\WoW.exe -opengl works perfectly, except I get these errors (I guees it's not so perfect :P)

```
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:import_dll Library GLU32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135
```

And the Azureus thing worked fine for one update, but the others got different errors. Screw Azureus, I'll get another client.

---

