---
title: "Creating Launchers for programs being run with wine"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-11-20
my hard drive has an ubuntu partition and a windows partition. their are a few programs on the windows partition i still like to run under ubuntu, namely photoshop cs2 and programmers notepad, with wine. 

i use these programs quite frequently and i am fed up with having to navigate to them and then open then with wine.

i was wondering if i could create launchers or desktop icons that would open these programs with wine. or add a launcher to my applications menu that would open these programs with wine.

Photo shop cs2 is located here:

 ```
/media/hda1/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe
```

and programers notepad is located here:

```
/media/hda1/Program Files/Programmers Notepad/pn.exe
```

```

```

---

### Post by qamelian on 2006-11-20
You should be able to create a new launcher and, in the line where you would normally have something like /usr/bin/my_app to launch a program simply enter ```
wine /media/hda1/Program\ Files/Adobe/Adobe Photoshop CS2/Photoshop.exe
```

---

### Post by Jamesbowden on 2006-11-20
It wont work, mabye its because their is spaces in the file location?

do i have to pick application, application in terminal, or file when i'm creating the lanucher?

---

### Post by CowzRule on 2006-11-20
I believe in the command box of your luancher you type wine followed by the location and name of the app you want to run inside quotes. So to launch Photoshop.exe type:
```
wine "/media/hda1/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe"
```

---

### Post by Jamesbowden on 2006-11-20
Perfect, Thanks alot

---

### Post by CowzRule on 2006-11-20
Glad I could help :)

---

### Post by thomasbechtold on 2006-11-20
hi,

you have to use wine "/media/hda1/Program Files/..."

Cheers Tom

sorry. saw the answers too late...

---

