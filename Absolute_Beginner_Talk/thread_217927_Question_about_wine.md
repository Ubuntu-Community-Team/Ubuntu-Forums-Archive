---
title: "Question about wine"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-07-17
I just installed Password agent.... it looks like it installed it perfectly....

Problem is, after I closed the program I could not find it... I even did a file system search for "password agent" but I cannot find "password agent.exe"....

anyway.... I am going back into war3 to get into a game with someone.... so I wont see any reply for at least a other 2-3 hours....

---

### Post by xXx 0wn3d xXx on 2006-07-17
> **IDontKnow9998 said:**
> I just installed Password agent.... it looks like it installed it perfectly....

Problem is, after I closed the program I could not find it... I even did a file system search for "password agent" but I cannot find "password agent.exe"....

anyway.... I am going back into war3 to get into a game with someone.... so I wont see any reply for at least a other 2-3 hours....

It should be under /home/USERNAME/.wine/drive_c/Program Files

---

### Post by IDontKnow9998 on 2006-07-18
> **xXx 0wn3d xXx said:**
> It should be under /home/USERNAME/.wine/drive_c/Program Files


Not there... in fact there is also no "program files" either (well excluding the other on my other HDD)...

---

### Post by nalmeth on 2006-07-18
What are the contents of ~/.wine

Since the installation of the app went fine, I suppose wine should be running fine, in which case your directories should be in place.

It is always recommended to run winecfg before using wine.

---

### Post by IDontKnow9998 on 2006-07-18
> **nalmeth said:**
> What are the contents of ~/.wine

Since the installation of the app went fine, I suppose wine should be running fine, in which case your directories should be in place.

It is always recommended to run winecfg before using wine.

".wine" is not found....  Also what changes would I do with wincfg?

---

### Post by nalmeth on 2006-07-18
None, unless you want wine to run a program thinking it's XP or ME or 2000 or something.

winecfg just creates all the directories, I believe.

Are you sure there is no hidden directory in your home folder called .wine?

(the period means the folder is hidden)

I don't know how you would be able to install an app with wine unless all the directories were carved out.

---

### Post by IDontKnow9998 on 2006-07-18
> **nalmeth said:**
> None, unless you want wine to run a program thinking it's XP or ME or 2000 or something.

winecfg just creates all the directories, I believe.

Are you sure there is no hidden directory in your home folder called .wine?

(the period means the folder is hidden)

I don't know how you would be able to install an app with wine unless all the directories were carved out.


ah, that was the problem... On top of that the .exe is called pwagent.exe :P

What is the trick to running these applications? Am I supposed to write the whole path every time?

---

### Post by IDontKnow9998 on 2006-07-18
I cant even access it because of the spaces...

---

### Post by nalmeth on 2006-07-18
yep, but with a shortcut you can make it really easy.

You can configure gnome (or KDE if you use that) to use wine for all .exe extensions. Right-click the .exe, go to properties, and configure it from there.

Or, just make a shortcut on the desktop as:
wine /location/of/launcher.exe

EDIT:: Re: Spaces
in the terminal, if a directory has a space, you add a \ right before the space. For example, assuming the problem directory is 'Program Files'
you would instead type it in as:
Program\ Files

Or, if you want to be lazy, use auto-completion.

Type in Program and hit TAB to let the terminal finish what you were typing, if the folder exists. If there are more than one folder with the same spelling at the beginning, hit TAB twice to display the options.

---

### Post by IDontKnow9998 on 2006-07-18
> **nalmeth said:**
> yep, but with a shortcut you can make it really easy.

You can configure gnome (or KDE if you use that) to use wine for all .exe extensions. Right-click the .exe, go to properties, and configure it from there.

and how exactly do I do from there :P ?

---

### Post by IDontKnow9998 on 2006-07-18
Anyone?

---

