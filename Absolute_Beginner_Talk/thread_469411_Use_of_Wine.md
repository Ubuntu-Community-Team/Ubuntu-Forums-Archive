---
title: "Use of Wine"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by God_of_Belac on 2007-06-09
Hi!
I installed wine and have been trying to follow the instructions here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_run_programs_in_Wine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_run_programs_in_Wine)

but I must be doing something wrong as the terminal can't find any of the programs I try to open.

Can anyone help me figure out how to navigate using the terminal to the location of a particular program?

---

### Post by taurus on 2007-06-09
You can use cd to change directory until you get to where you plan to be.

```
cd **destination**
```

---

### Post by teddybairs1 on 2007-06-09
I usually use winefile to launch my windows programs in wine. It's just that much easier.
Generally, wine installs all programs to /home/[username]/.wine/drive_c/
In the terminal, you can specify the directory name in either linux or windows format. For example, the launcher for Starcraft can look like either this:

wine /home/[username]/.wine/drive_c/Program\ Files/Starcraft/Starcraft.exe

or this

wine "c:\Program Files\Starcraft\Starcraft.exe" (The quotations are necessary in this format.)

If you're trying to launch a windows file not located in the .wine directory you need to know the path name. It is often easier to just cd into the directory where the executable is located. For example, under Feisty, my Windows partition is sda2 so to launch Solitaire under wine it would look like

wine /media/sda2/windows/system32/sol.exe

or

wine "d:\windows\system32\sol.exe"

Where wine recognizes my windows partition as drive "d:"

In any event, wine doesn't create symbolic links for it's programs into the home directory so you have to know where the executable it located. This is why I generally use the winefile file manager because it can give you a better idea where everything is.

---

