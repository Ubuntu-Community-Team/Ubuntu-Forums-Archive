---
title: "need some help with wine"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-05
aight, so i just installed wine through synaptic, and now i downloaded an exe file (steam to be exact) and have no idea how to make it work with wine? can somone perhaps tell me what steps i need to take to make it start installing?
thanks

---

### Post by bodhi.zazen on 2006-09-05
Perhaps. What did you download and to where?

In general, in a terminal:
```
[color=red]wine path_to/steam.exe[/color]
```

---

### Post by orb9220 on 2006-09-05
Saw a multiple steam threads in games section.

---

### Post by crunchystrike on 2006-09-06
no, i need to create the fake C: and i dont know how to do that

---

### Post by bodhi.zazen on 2006-09-06
in a teminal
```
winecfg
```
The exit.

---

### Post by Mimsy on 2006-09-06
You can probably get some help from the HOWTO forum too, there is a thread there with step-by-step instructions on how to set up Wine and create the fake c:\

If a n00b like me can get through it and not break anything, anyone should be able to. ;-)

/Mimsy

EDIT: I need help installing things under Wine instead. It won't let me switch to CD two during the install! :confused:

---

### Post by crunchystrike on 2006-09-06
alright, now where can I find the fake C:

and also what would I need to type if the file was on the desktop called SteamInstall.exe?

---

### Post by bodhi.zazen on 2006-09-06
> **crunchystrike said:**
> alright, now where can I find the fake C:

and also what would I need to type if the file was on the desktop called SteamInstall.exe?

LOL

Check you home directory for a hidden folder ".wine"

```
 wine /home/user_name/Desktop/SteamInstall.exe
```

---

### Post by crunchystrike on 2006-09-06
dang, when I go to home folder, i cant see no .wine

---

### Post by kingtutt on 2006-09-06
try 'ls -a' to see "hidden" file/directories, ones that start with .*

---

### Post by bodhi.zazen on 2006-09-06
> **crunchystrike said:**
> dang, when I go to home folder, i cant see no .wine

1. Try running the wine command anyway.

2. In a terminal type:
```
ls -a /home/user_name | grep wine
```

Do you see .wine?

If you are using nautilus enable the "show hidden" option.

---

