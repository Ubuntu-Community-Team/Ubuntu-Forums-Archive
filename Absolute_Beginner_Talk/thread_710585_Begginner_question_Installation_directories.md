---
title: "Begginner question: Installation directories"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by ShadouX3 on 2008-02-28
Hi there, sorry for beginner question.. I recently [as in today] moved from windows to ubuntu 5 (Since I couldnt get 7 to work, and I already had disk 5 from before) and since I again couldnt get the universe thingy repository to work, I downloaded the WINE .deb file for Breezey from their homepage

I installed it with the following command:
dpkg -i Desktop/Wine.deb [i think that was it]

anyway I've found files in /usr/bin called Wine so I assume its installed and I've been able to use winecfg from the terminal so I take that as another indicator its installed... but a guide I'm using on how to install a program with wine says I need to copy two DLLs which I downloaded to the following directory:



~/.wine/drive_c/windows/system32/

but I cant seem to find out where that directory is?

again I know this sounds kinda silly, but would appreciate any help, ty

---

### Post by Crooksey on 2008-02-28
```

$ cd ~/.wine
```

Does that not work?

Ubuntu, release 5 is now *i think, unsupported.

---

### Post by sisco311 on 2008-02-28
[FONT=monospace]~/.wine is a hidden folder in your home directory.
Press Ctrl+h in your file browser or select Show Hidden Files from the menu.
[/FONT]

---

### Post by ShadouX3 on 2008-02-28
Hm, I imagine 5 uses the same file installation directories as 7 though right? anyways yup it works in the terminal but am trying to find how to get to it from the Applications > Accessories > File Browser so I can drag and drop the 2 DLL's from the desktop straight to the folder, since I'm not entirely sure of how to do that from CLI

EDIT:
> **sisco311 said:**
> [FONT=monospace]~/.wine is a hidden folder in your home directory.
Press Ctrl+h in your file browser to see hidden files and directories.
[/FONT]



thankyou!!

---

### Post by sancho panza on 2008-02-28
I dunno if I fully understand your question, so pardon me if im wrong:
~ always refers to your home directory. ie /home/username/
and directories starting with a dot (.) are hidden directories.
You can access the wine directory with the command cd .wine/ from you home directory.

Does that answer ur query?

---

### Post by ShadouX3 on 2008-02-28
> **sancho panza said:**
> I dunno if I fully understand your question, so pardon me if im wrong:
~ always refers to your home directory. ie /home/username/
and directories starting with a dot (.) are hidden directories.
You can access the wine directory with the command cd .wine/ from you home directory.

Does that answer ur query?

yup ty ^^

---

