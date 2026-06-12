---
title: "Wine- how do you use it?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by punkypine on 2007-04-22
so i just installed wine on my computer... but i have no idea how to run an application through it. i double click the icon in the apps folder and nothing happens. i also tried to run some programs on my NTFS portion of the hard drive and i got an error

do programs have to be on the linux portion of the hard drive to be run? (that would suck, i dunno if i have enough space for 2 installs)... and how exactly do you run programs in wine?

---

### Post by eyelessfade on 2007-04-22
since most windows programs need a registry to run, you need to install them with wine.

just wine Install.exe or so.
then it will install the program (hopefuly) and you can start the program with wine program.exe

take a look at winehq.org for more info on programs.

keep in mind that not all programs will work.

---

### Post by raja on 2007-04-22
Wine is not a surefire way to run any windows application. The reliability varies with each application. Some may not even have to be installed in wine itself, while some may have to be installed. Check out about the application at  the wine site. An application like wine tools or wine doors may also help.

---

### Post by punkypine on 2007-04-22
ok lets say i have the exe file on my desktop.... i double click it and it gives me an error... i hit "open with" and wine isnt on the program list... how exactly do i start the program through wine?

edit: the program is guild wars, which it says should work both in these forums and on the apps db

---

### Post by raja on 2007-04-22
You can select open with other application, choose custom command and type 'wine' there. Else you can navigate to the folder in the terminal and type ```
wine programname.exe
```

---

