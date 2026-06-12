---
title: "How to install from cdrom using wine! Help!!"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Clipz on 2006-03-14
Hi i need desprete help on how to install a software using wine from a cd that i have

---

### Post by mavr on 2006-03-14
Does the cd have the setup.exe? u just have to run that with wine, from console

wine /media/cdrom(or wathever)/setup.exe and it should go like that

---

### Post by Clipz on 2006-03-14
i did that but nothing happens it just goes to the next line

---

### Post by mavr on 2006-03-14
ubuntu or kubuntu? Cause on gnome there is a graphical tool for Wine, that might be more helpful in telling you what went wrong. I tried it on KDE as well but it crash pretty often. Give that a try.

---

### Post by Clipz on 2006-03-14
Well im using ubuntu i tried doing the winecfg thing that didnt work either

---

### Post by Clipz on 2006-03-14
im trying to install the software for the Avermedia DVD EZmaker PCI, the drivers are installed but the software to use it is not installing

---

### Post by mavr on 2006-03-17
I don't know what is it :p
Try using cedega. Is not free.

---

### Post by CameronCalver on 2006-03-18
When i want to run an exe this is what hapens

broadband@Bird2Fish:~$ wine c"/programfiles/nitto/nitto.exe
>


that morethan sign comes up>>

---

### Post by matthewv on 2006-03-18
Pretty sure this is because you have left an open quote in your command:
```

wine c***"***/programfiles/nitto/nitto.exe

```
The **>** sign pops up because the terminal expects you to close the quote... ie you have an incomplete command

---

### Post by CameronCalver on 2006-03-18
how will i end it then

---

### Post by chuckyp on 2006-03-18
[QUOTE=CameronCalver]how will i end it then[/QUOTE]
Well the " shouldn't even be in there in the first place the proper way would be wine /pathto/program/whatever.exe  no need for the " mark.

---

### Post by CameronCalver on 2006-03-18
when i want to install myob a acconting program it says unable to install installdriver instance code......

---

### Post by chuckyp on 2006-03-18
Wine is not free of bugs etc... I would check the appdb as provided by another poster and see if your specific application is supported.  If its not listed you could still try it and see if you can get it working.  If all else fails there is a #winehq channel on freenode some of the people around there may be able to help.

---

### Post by YokoZar on 2006-03-18
[QUOTE=CameronCalver]When i want to run an exe this is what hapens

broadband@Bird2Fish:~$ wine c"/programfiles/nitto/nitto.exe
>


that morethan sign comes up>>[/QUOTE]
Replace the " with a :

---

### Post by CameronCalver on 2006-03-18
[QUOTE=chuckyp]Wine is not free of bugs etc... I would check the appdb as provided by another poster and see if your specific application is supported.  If its not listed you could still try it and see if you can get it working.  If all else fails there is a #winehq channel on freenode some of the people around there may be able to help.[/QUOTE]
Hey What is appdb and can i get onto #winehq on xchat irc and how

---

