---
title: "[SOLVED] How do I make a link to a command?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by coront on 2007-08-03
Hey everyone, is there a way to make an icon that executes the command "wine myprogram.exe"??? I just need it to run that command in a simple way ++Double click ==> my program runs++ :D. Thank you

---

### Post by aysiu on 2007-08-03
Well, you right-click on the panel, select *Add to Panel* and *Custom Application Launcher*. For the command part of the launcher, put in ```
wine myprogram.exe
``` or whatever code launches the program.

---

### Post by HermanAB on 2007-08-03
Here is the crude way:
You need to change directory to spot in the filesystem where myprogram.exe resides, then run wine with myprogram.exe as a parameter.

First find out where the heck myprogram.exe is:
find / -name myprogram.exe

Now find out where wine is:
find / -name wine

On your desktop, create a new text file (script) and call it whatever:
#! /bin/bash
cd /where/ever/the/hell
/where/ever/wine myprogram.exe

Make the file executable:
chmod 754 whatever

Run it:
Double click the file icon on the desktop

'Hope that gives you some ideas!

Cheers,

Herman

---

### Post by kyphi on 2007-08-03
Yes.  Right click on top panel, go to Add to Panel and click on Custom Application Launcher.

Then give it a name, enter the path to the programme and give it an icon.

---

### Post by HermanAB on 2007-08-03
It is not as simple as that with wine.  

In order to run a windoze application with wine, you need to execute two commands.  Therefore a simple desktop link to wine isn't enough.  You can start by making a simple desktop link to wine, but then you have to go and edit the thing to make the two steps required: change directory to the application, then invoke wine with the application as a parameter.  Separate the two steps by a semi-colon.

---

### Post by aysiu on 2007-08-03
> **HermanAB said:**
> It is not as simple as that with wine.  

In order to run a windoze application with wine, you need to execute two commands.  Therefore a simple desktop link to wine isn't enough.  You can start by making a simple desktop link to wine, but then you have to go and edit the thing to make the two steps required: change directory to the application, then invoke wine with the application as a parameter.  Separate the two steps by a semi-colon.
I haven't had that experience. I've been able to launch Wine apps with one command by specifying the path: e.g. ```
wine "z:\home\*username*\.wine\drive_c\Program Files\Filezilla\Filezilla.exe"
```

---

### Post by HermanAB on 2007-08-03
Interesting - I haven't tried that with wine recently.  Back in the bad old days, things would not work unless the windows program was launched from its 'home' directory, so I do the 'cd' then run out of habit!

Cheers,

Herman

---

### Post by asmoore82 on 2007-08-04
yea, wine should always be lauching programs that are installed in its fake C: drive
AND wine automagically knows how to launch these programs without the need to
worry about Current Working Directory stuff.

that last example:
```
wine "z:\home\*username*\.wine\drive_c\Program Files\Filezilla\Filezilla.exe"
```

should look like this:

```
wine "C:\Program Files\Filezilla\Filezilla.exe"
```

and you're golden

---

### Post by aysiu on 2007-08-04
Well, I don't know what it *should* look like, but the line with z: has always worked for me.

---

### Post by asmoore82 on 2007-08-04
now that I think about it there should be an option in WINE that locks it down so that
WINE can *only* run .exe's from its fake C drive.
this would help those poor unfortunate souls who are destined to get a virus.

---

### Post by coront on 2007-08-04
THanks for all the help. It works perfectly :D

---

