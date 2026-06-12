---
title: "How to use wine?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-10-04
I just got wine to use a few windows apps. I was just wondering how to use it.

---

### Post by Crooksey on 2006-10-04
sudo apt-get install wine

then double click a .exe, and open with a custom command of "wine" :-)

---

### Post by spyker3292 on 2006-10-04
Thanks, I'll try that.

---

### Post by Ambimom on 2006-10-04
download the windows file you want...then navigate to it.  

Right click Windows.exe and you'll see in the menu something like "Open with Wine Emulator"

click on that.

Or go to the Windows.exe file and right click on "Properties".  Go to the Open With tab and add Wine.

Caution:  Wine works, but not with everything, or sometimes only partially.

---

### Post by peabee on 2006-10-04
I managed to get this working last night (and I'm not expert).  I installed Wine, opened a terminal thing, then typed wine and dragged the file (it was on the desktop) to the end, it put in the path and hey presto.  
Turns out it wanted IE5 but at least it worked :)
P

---

### Post by 3rdalbum on 2006-10-04
Best to start up the program from a terminal, at least for the first time you use it.

*cd* into the directory that has the program (let's call it "myapp.exe") and go:

```
wine myapp.exe
```

If the program won't run under a normal Wine installation, you will probably see errors being put into the terminal window, mentioning that certain DLL files could not be found. Find these from your Windows partition and put them into ~/.wine/drive_c/windows/system/, then try Wine again.

When you know that the program can be run without problems, then it's fine to double-click it.

---

### Post by 3rdalbum on 2006-10-04
> **peabee said:**
> I managed to get this working last night (and I'm not expert).  I installed Wine, opened a terminal thing, then typed wine and dragged the file (it was on the desktop) to the end, it put in the path and hey presto.  
Turns out it wanted IE5 but at least it worked :)
P

[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

---

