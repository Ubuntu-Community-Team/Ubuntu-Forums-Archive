---
title: "issues with alltray"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-05-06
FIRST ISSUE

i'm using gnome & alltray, but i can't get this to work. Sad
alltray /home/gail/javaop/Core/JavaOp2.jar as a launcher Application or Application in Terminal command dont work. making a link dont work either since i cant seem to modify the command... and doing alltray /home/gail/javaop/Core/JavaOp2.jar gives an error:

```

gail@badassness:~$ alltray /home/gail/javaop/Core/JavaOp2.jar
/home/gail/javaop/Core/JavaOp2.jar: 3: Syntax error: ")" unexpected

```

putting sudo before that command makes no difference.

then i tried using

```

alltray "java -jar ~/javaop/Core/JavaOp2.jar"

```

& got unable to execute file.

is there any way i can make this program start up minimimzed ? it takes aike 30 seconds off my morning routine to start it up :P

SECOND ISSUE:

i can start thsi program up manually by double clicking the .jar file, then i go to applications.alltray and minimize it & its all good except for one problem. after it minimizes it doesnt go to the notification area next to gaim like it use to. it just dissapears & i don't know how to bring it up ag ain. i know the program is still running cuz i go onto bnet with a game & go to my channel & the bot is still there...

i tried to add/remove notification areas thinking i removed something by mistake but i guess they're still there.... how do i get the alltray/javaop thing back on notification area so i can sue the program?

ty for any help & hope this made sense, if u need more info let me know.

---

### Post by matburton on 2007-05-07
Hey,

I'm using alltray as well (and loving it)
If you didn't I'd recommend installing it through this repository:
[[COLOR="Blue"]http://asher256-repository.tuxfamily.org[/COLOR]]("http://asher256-repository.tuxfamily.org")

Anyway to start something minimized simply don't use -s
so
```
alltray gnome-terminal
```
will not show the terminal at start-up but this will
```
alltray -s gnome-terminal
```

Also -na gets rid of "Alltray" in the title bar and -i <path> allows you to set your own icon.

Is that jar suppost to run in a terminal? Or does it have a GUI?
If its the former then you must use this:
```
alltray -na "gnome-terminal /home/gail/javaop/Core/JavaOp2.jar"
```
or something similar to get it going in the terminal

for instance I have this for recording net radio while I'm working for later:
```
alltray -na -s "gnome-terminal --window-with-profile=Ripper --hide-menubar -x streamripper $Stream -d /home/mat/Downloads/StreamRip -s -o never -k 1 -D \"%A - %T\""
```
note that this needs a terminal so alltray runs the gnome-terminal which executes everything after the -x

Thought I'd post all that even if it isn't helpful for you for anyone else that finds this thread ;)

Sorry can't help with the second issue, if you didn't use the repository then you could try a reinstall from there? Just a shot in the dark!

---

### Post by lunaz on 2007-05-08
ty for the info :)
i did try alltray -s /home/gail/javaop/Core/JavaOp2.jar and alltray -s "/home/gail/javaop/Core/JavaOp2.jar" then restarted x, but it didn't start the program for me. :(

this program runs off a swing gui, its a battle.net chat bot :P

---

