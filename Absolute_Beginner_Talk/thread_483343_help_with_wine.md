---
title: "help with wine"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by timelord29 on 2007-06-24
i think i installed wine on my computer but im not sure. i went though the install process and i didnt get any errors but i cant find it anywhere to start the program. it appears in the add/remove thing but its not letting me do anything with it. help?

---

### Post by BobCFC on 2007-06-24
Try running an exe file with it from the terminal such as

wine /mywindows/myprogram.exe


Once you know it works you can click on an exe and open it with wine like a document.

---

### Post by mc4man on 2007-06-24
i can give you a suggestion to help ease your way into using the terminal and wine
click places on the top of your screen
click computer then doubleclick filesystem
click view look down and click show hidden files
find home folder, double click and then doubleclick folder with your name
scroll down and find .wine folder
right click and select make link
this will create a link to .wine  find it and drag and drop on desktop
when you double click the link you'll gain access to drive_c where you can install programs from and later run from program files or whatever

edit:before you do anything I'd suggest running winecfg  open terminal and type in winecfg, press enter

---

### Post by Crafty Kisses on 2007-06-24
> **timelord29 said:**
> i think i installed wine on my computer but im not sure. i went though the install process and i didnt get any errors but i cant find it anywhere to start the program. it appears in the add/remove thing but its not letting me do anything with it. help?

Usually when you right click on the program it will say like "Emulate With Wine" here's a screenshot:
[img]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-11.png[/img]

---

### Post by shifty_powers on 2007-06-24
Two things.

Firstly, to find out your version of wine, indeed if you have it installed at all,

```
wine --version
```

and also,

```
winecfg
```

needs to be run when you first install wine, it will then set up the ./wine directory in your /home directory

---

### Post by normworthy on 2007-06-24
I have a similar problem.....

I typed winecfg and got a menu form. I messed with it a bit and it did nothing. 
I have the .wine folder, I have a link to .wine on my desk top.
I found notebook.exe and explorer.exe. if I press notebook.exe it says "No suitable application"
I figure if it can't so that (which Ipresume came with the wine pacage, it won't have a hope of running my programs

---

### Post by BobCFC on 2007-06-24
If you right click on the exe do you get the menu like the picture above?

---

### Post by normworthy on 2007-06-24
No, if I right click, I get the standard choices it has "open with ....." but wine is not one of the choices

---

### Post by ts51 on 2007-06-24
Click open with, then type wine in one of the boxes (sorry on xp right now don't know exactly where )then hit OK and see if that works. 

Also, you could see if it is working by just typing "wine notepad" [EDIT: In the terminal]... I did that to verify it was working correctly.

---

### Post by Nekiruhs on 2007-06-24
> **Codename said:**
> Usually when you right click on the program it will say like "Emulate With Wine" here's a screenshot:
[img]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-11.png[/img]
That only happens when they install through Automatix2. They'll have to right click, goto properties, then select the Open With tab, type wine in the box and click ok.

---

### Post by normworthy on 2007-06-24
OK, perfect, that worked , I right clicked the exe program, went to properties, tab for open with and wrote wine.
then I went to my disc and found the setup.exe and it already said wine in it. I clicked and it said it would set it up.

I trust this is the way to do it now:
Put in a windows program disc, click on the setup or instal and it will let me install the program and run it as if I was running windows.

If that is right, thank you very much
Norm

---

### Post by Crafty Kisses on 2007-06-24
> **Nekiruhs said:**
> That only happens when they install through Automatix2. They'll have to right click, goto properties, then select the Open With tab, type wine in the box and click ok.

Gotcha.

---

