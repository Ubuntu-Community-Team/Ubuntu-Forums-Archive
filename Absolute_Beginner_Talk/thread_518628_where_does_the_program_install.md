---
title: "where does the program install?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by bibas on 2007-08-06
i downloaded a ubuntu package of WINE .. and installed ...but it appears to be nowhere.
where is the program located? or the shortcut?..

I am so happy with the prompt replies i get of the every threads i posted.
god bless u guys.

---

### Post by proalan on 2007-08-06
contents of wine are hidden in your home folder

open / home/your_account in nautilus

then press ctrl+H to reveal hidden folders, it should be listed as .wine

or in a terminal do

ls -a ~

---

### Post by Hallvor on 2007-08-06
[removed]

---

### Post by muep on 2007-08-06
If you are wondering where wine itself is located, you can run 
```
whereis wine
```
in Terminal to see where it is. the "C" disk of wine is located as default under your home dir, in ~/.wine/drive_c/

Usually, when you want to run a windows program, you open a terminal, cd to the directory where the program is and run it like this:
```
wine programname.exe
```

You may want to check a program named winecfg to see some of the most important wine settings. Just run winecfg from the Terminal.

---

### Post by crazydiver on 2007-08-06
try running winecfg on the terminal.

---

