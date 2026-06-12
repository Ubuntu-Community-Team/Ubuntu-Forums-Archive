---
title: "can't uninstall files installed with wine"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-27
Can't find wine anywhere yet I can install programs with it but if there is no desktop icon I cant launch it fom menu. I had mandrake 10.2 kde and wine showed up on menu, is gnome different? How do I get rid of files installed by wine if I can't find wine on menu? I really need to make the "point and click" way work for wine if I'm going to "convert" my friends who use microshaft!!!!

---

### Post by mustang on 2006-03-27
It's my understanding that installing a program with wine does not touch anything outside the wine "windows drive." Thus, deleting the folder on your wine "windows drive" containing the program would probably be enough to get rid of the program.

Someone please correct me if I'm wrong.

---

### Post by xhie on 2006-03-28
[QUOTE=wolfee]if there is no desktop icon I cant launch it fom menu[/QUOTE]

To lauch something you installed with wine:

wine "/home/yourname/.wine/drive_c/Program Files/name of thing"

you can create a laucher for your program if you so desire for any menu or the desktop.

[QUOTE=mustang]deleting the folder on your wine "windows drive" containing the program would probably be enough to get rid of the program.[/QUOTE]

Thats what I do, dunno though I could be totally wrong and theres a better way to do it.

---

### Post by wolfee on 2006-03-28
Thanx!! I 'm really happy with Ubuntu although some thngs in Mandrake 10.2 where nice too. How do I create a launcher program for menue?

---

### Post by mustang on 2006-03-28
[QUOTE=wolfee]Thanx!! I 'm really happy with Ubuntu although some thngs in Mandrake 10.2 where nice too. How do I create a launcher program for menue?[/QUOTE]

Type in

```
smeg
```

and click on new entry. In the command field, you'd have something like "wine "/home/yourname/.wine/drive_c/Program Files/name of thing"

---

