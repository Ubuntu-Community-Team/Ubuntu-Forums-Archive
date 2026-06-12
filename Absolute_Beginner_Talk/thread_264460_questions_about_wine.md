---
title: "questions about wine"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by IusedTObeSOMEONEelse on 2006-09-24
I have wine set up and I know it works as I have used my games from Game House. I have one game in particular that goes through the wine set up but when I click the icon I get a flash screen and then nothing happens. Am I missing something? It's a simple game (MahJong Medley) so it doesn' require alot of extras.I know there is the one mahjong game in linux, but is there also some where a more of a variaty of mahjong games that will work for linux?

---

### Post by deadgobby on 2006-09-24
Try running wine from the terminal and see what error it brings up when you try to run the game in question. It just may not run at all.

---

### Post by bodhi.zazen on 2006-09-24
First you can run MahJong native.

```
sudo aptituide install mah-jong
```

Beyond that see [wine HQ](http://appdb.winehq.org/)

Put your appy in the gray (search) box on the Left.

---

### Post by IusedTObeSOMEONEelse on 2006-09-24
Can u please clarify "'run wine from terminal" as I am fairly new and I don't want to mess things up.

---

### Post by IusedTObeSOMEONEelse on 2006-09-24
please can some one assist/

---

### Post by comppsyco on 2006-09-24
"run wine from terminal" simply means that in a terminal (for information about what the terminal is, visit [www.linuxcommand.org](www.linuxcommand.org)) type:```
wine
``` followed by the program location/name.

EDIT: By the way, it's considered rude to bump your own thread.

---

### Post by HereInOz on 2006-09-24
Perhaps rude to bump, but then they did wait almost an hour.  Unlikely that anyone would have seen the question after that time if it had not been bumped.  Fairly understandable action.

---

### Post by deadgobby on 2006-09-25
lets say you save the exe file on the desktop. Then you open up your terminal
by going to Applications>Accessories>Termainal

When the terminal is open. 

Lets go to the desktop area by going through the terminal. Becuase we are saying that you saved the exe file for you game is at.

So type in 

g$ubuntu:~/cd Desktop

g@ubuntu:~/Desktop$ wine MahjongMedleyInstall.exe

 You may get this error as I got
 Unhandled page fault on write access to 0xa164003d at address 0x3001be2a (thread 0024), starting debugger...
 And a buch of codes. Basicaly it is telling you. No I'll will not run using wine. 

 Remember that wine cannot not run all of micro s programing code. It would be great, but wine will not be free any more. 
Gobby

---

### Post by IusedTObeSOMEONEelse on 2006-09-25
~$ g$ubuntu:~/cd Desktop
bash: g:~/cd: No such file or directory               This is what came up now I have the download window up with the file on it and also its on my desktop. When I look at properties for file it say "Name: Mah Jong Quest   Type: desktop configuration file  Size: 319 bytes  Location: /home/sally/desktop  MIME type: application/x-desktop                            So I know Ihave the file

---

### Post by CatKiller on 2006-09-25
I think that the file you have on the desktop is not the file but a shortcut to the file. The MIME type: application/x-desktop is not the right type for what you want. When you've got the right file it will say MIME type: application/x-ms-dos-executable.

The commands that you need don't include the prompt that deadgobby included. It would just be ```
cd Desktop
wine MahjongMedleyInstall.exe
```

---

### Post by deadgobby on 2006-09-25
Sorry to put the terminal prompt, I thought it may help you.
Gobby

---

