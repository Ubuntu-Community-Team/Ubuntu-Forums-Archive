---
title: "basic command question"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-07-13
ok so i need to execute a program using wine, what would be the best way to do this from the command line the file is located at:

/home/m/Desktop/Link_to_.wine/drive_c/ProgramFiles/buzz/buzz.exe

---

### Post by Nythain on 2007-07-13
put wine in front of that

---

### Post by FleetAdmiral74 on 2007-07-13
Tis is not the command line..sorry, I'm not that advanced. But if you right click the file, properties, and have it open with a custom command, wine, it should work fine.

---

### Post by thelegionnaire on 2007-07-13
im specifically looking for the command line, thanks tho

---

### Post by Nythain on 2007-07-13
seriously its as easy as
```

wine /path/to/whatever/app.exe

```
so using the path you gave (wich looks kind of weird, the standard would be more like ~/.wine/drive_c/Program\ Files/buzz/buzz.exe but thats besides teh point) would look like this in terminal
```

wine  /home/m/Desktop/Link_to_.wine/drive_c/ProgramFiles/buzz/buzz.exe

```
alternately you could cd into the directory containing the exe and type just wine whatever.exe like this
```

cd /home/m/Desktop/Link_to_.win/drive_c/ProgramFiles/buzz/
wine buzz.exe

```

---

### Post by RomeReactor on 2007-07-13
Hi. I think the correct path would be:
```
wine /home/m/.wine/drive_c/ProgramFiles/buzz/buzz.exe
```
Just make sure that **ProgramFiles** is the correct name for the folder (I think it's actually **Program Files**), in which case the command would be:
```
wine /home/m/.wine/drive_c/Program\ Files/buzz/buzz.exe
```
as **Nythain** suggested.

Although **FleetAdmiral74**'s suggestion seems more practical.

---

### Post by Nythain on 2007-07-13
> **RomeReactor said:**
> Hi. I think the correct path would be:
```
wine /home/m/.wine/drive_c/ProgramFiles/buzz/buzz.exe
```Although **FleetAdmiral74**'s suggestion seems more practical.
just a note on the right click menu option.
you wont get any output in a terminal (wich is very usefull for debugging crashes) and the user might be trying to write a desktop link or shell script to run something

---

### Post by thelegionnaire on 2007-07-13
im actually trying to use the gdesklets starterbar, so i got that working, now how can i view the contents of a drive in nautilaus through a command line?

---

### Post by Nythain on 2007-07-13
ummm... for futher command line tips you should search the forums here for "command line tips" or "command line commands" or search google for something similar like "linux bash commands" or "linux command line commands" or "linux command line tutorial" and you will get results with many of the more frequently used commands, like cd, cp, mv, mkdir, rm, rmdir, ls, and the likes...

not sure if you can view the entire contents of a drive all at once, but you can certainly use the ls command to view teh contents of a directory, and use the cd command to move from directory to directory

popular ls options
ls -a (lists all files, including hidden ones)
ls -l (lists files with long detailed info)
so ls -al would list all files in a directory and give detailed info about them

---

### Post by thelegionnaire on 2007-07-13
im basically trying to make a shortcut on the starterbar that would open my hard drive in the window manager, ya know, so i can view my stuff, much like clicking the HDA1 icon on my desktop

---

### Post by Nythain on 2007-07-13
i would try
```

nautilaus /path/to/where/you/want/to/open/

```
like
```

nautilaus /

```
might work to open it at root whereas
```

nautilaus /media/

```
should theoretically work to open up your media directory
i dont use gnome or nautilaus so im not sure if thats how it works, but that would work for konqueror
and if you want to open a location with root permission
```

gksu nautilaus /media/

```
would popup the password window then open nautilaus with root permissions

---

### Post by RomeReactor on 2007-07-13
You could also check out [LinuxCommand]("http://www.linuxcommand.org/").

---

### Post by Nythain on 2007-07-13
you just shrunk my bookmarks by like five urls with that one site... thanks... i like how it covers the commands, shell scripting, man pages and more

---

### Post by eldepeche on 2007-07-13
Nythain's suggestions above are correct, but it's actually spelled "nautilus."

---

