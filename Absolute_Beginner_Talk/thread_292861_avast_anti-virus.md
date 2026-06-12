---
title: "avast anti-virus"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-11-04
ok folks i have a simple question that i hope will come back with a simple answer so here goes.
earlier this morning i downloaded and installed avast on my dapper computer.
where the heck is the icon for it?
i typed avast in the terminal and then i registered it but where is the ICON?
Please somebody help tell me that im not goint insane and that everything will be ok!](*,) 
so anyhow any help would be grly excepted.

---

### Post by Ecthelion on 2006-11-04
I don't get it...

Do you just want to start the program...
Just type
```
avast
```
in terminal

Else... Dunno what you want

there is no icon for it...
you always have to run it from command line

---

### Post by Linux&amp;Lizards on 2006-11-04
oh! ok yeh i knew the code for it i just thought there must have been an icon for it somewhere any how ty.


thread no longer needed! :)

---

### Post by Ecthelion on 2006-11-04
> there is no icon for it...
you always have to run it from command line

You can make an Icon for it ... right click on the menu's and click "configure menu's"
then new item...

---

### Post by annda on 2006-11-04
or create your own shortcut - it's called a launcher. right-click on your desktop or panel and "create launcher" or "add to panel" -> "application launcher". the command you want is of course "avast". good luck!

---

### Post by Ecthelion on 2006-11-04
> or create your own shortcut - it's called a launcher. right-click on your desktop or panel and "create launcher" or "add to panel" -> "application launcher". the command you want is of course "avast". good luck!

that's what I meant...:D 
I have no English system so sometimes I use the wrong therms..
sorry for that

---

### Post by Linux&amp;Lizards on 2006-11-04
> **Ecthelion said:**
> that's what I meant...:D 
I have no English system so sometimes I use the wrong therms..
sorry for that

kk ty :) :)

---

### Post by meney on 2006-12-25
The Command to run the graphical interface of avast is
```
avastgui
```
After you run the avast install, open up the terminal and run this code to install the icon's and the link in app's -> accessories
```
cd /usr/lib/avast4workstation/share/avast/desktop && sudo ./install-desktop-entries.sh install
```

---

### Post by Mark Gillis on 2007-02-20
Forgive me for resurrecting a dead thread...But what you did with Avast! I would like to do with rkhunter and chkrootkit. Can I put them on a KDE desktop for easy access? BTW, You guys run a great community and even though I am a newbie, I have managed to make the transition from windows to linux just by reading how-to's, and responses to other newbie questions, and checking a book from time to time. Thanks.

---

### Post by Linux&amp;Lizards on 2007-02-20
I just was ok with running it with the commandline, that is where my experiance with it ended.

---

