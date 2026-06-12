---
title: "wine package won't install on my menus"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Bannor on 2007-06-07
I have both ubuntu and xubuntu

I have an updated wine version downloaded with synaptic manager,  and it won't add to my list of programs in my menus.  When I search for it in xubuntu I can find it and manually add it to the menus, I end up finding a laundry list of programs associated with wine,  unfortunately I am new to ubuntu and even newer to wine so I don't know what to add the the folder to make my windows programs work.  Also since everthing else automatically updates, and as mentioned earlier I am new,  I am conserned that this might be a symptom of a different problem.  Also of note, when I look up wine on my list of installed programs it is there, with the correct version but the coloring is opaic.

xubuntu 
laptop 
pentium 1gig
ram 192
version 7.04

ubuntu 
desktop
amd64 x2
ram 2gig
version 7.04

---

### Post by empthollow on 2007-06-07
i dont have wine in my program menu either.  it's not really something you can run on it's own, ubuntu automatically associates .exe files with wine as it is an emulator for windows protocol.  from a command line you would type something line ```
wine game.exe
```
wine installs defaultly to ~/.wine/drive_c    - from there you will see the windows directory structure.  find any .exe file and double click.  you can create a shortcut in the menu if you like, right click on menu and edit

---

### Post by NeoLithium on 2007-06-07
Have you already run ```
winecfg
``` in a terminal window?
Sometimes it's also hidden by default, you can take a look in the menu editor to see if its there but unchecked as well (System -> Perefences -> Menus)

---

### Post by Bannor on 2007-06-07
I found another post to that effect,  the first time I installed there was a wine group in my menus and that is the confusion. If i click on a program in my windows partition it will automatically run with wine?(assuming it is compatable)

---

### Post by Bannor on 2007-06-07
Also thank you

---

