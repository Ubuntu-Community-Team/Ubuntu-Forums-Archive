---
title: "error while trying to install World of Warcraft"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by suzyweb on 2007-10-20
Hello,

Thanks so much for this forum and all of your kindness.

I am really new to Linux. I've been a Windows XP user so please be gentle! :)

I'm trying to install World of Warcraft and I am following the directions that are located here:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

So far everything has worked until I get to the part where is says:
wine Installer.exe

When I enter it into the command line, I get this error:
wine: could not load L"c:\\windows\\system32\\Installer.exe": Module not found

I followed all the directions and have had no problems except for this. How do I make sure that the module is there? If it's not there then what did I do wrong?

I am running the 64bit version of Ubuntu. 

Thanks so much for your help! :)

---

### Post by Qwerty_ on 2007-10-20
You have to cd (change directory) to where the installer.exe file is.

should be

```
cd /cdrom
```

then run ```
wine installer.exe
``` there.

---

### Post by doomster on 2007-10-20
when typing wine installer.exe wine searches the default folder c:\\windows\\system32\\ witch is exactly /home/username/,wine/c/windows/system32/  for the installer.exe, the wow installer


in order to work you should run

 ```
wine /path/to/wow/installer/installer.exe
```
 :)


or for an easier way, go through GUI to the exact wow installation folder, right-click on installer.exe and choose Open with Application...  and use wine to do so

---

