---
title: "Configure Wine"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-17
I was playing around with my system when I ran across an EXE windows file. I clicked it for fun and for some reason wine started and installed it. I thought I didn't have wine and checked and saw I had it. Now when I try to access the program thorugh the terminal, I can't. What's the command to access them. I've been typing wine XXXX then the name of the program and it doesn't open. Where exactly did that program install itself to and how do I access it. If also possible, I want to be able to play some of my native windows games. How do I configure wine to do that?

;):h34r: Jaygo333 ;):h34r:

---

### Post by matthewv on 2006-01-17
The program has most likely installed itself to ~/.wine/drive_c/Program\ Files/
The drive_c folder created in a hidden folder in your home directory basically acts like your windows c: drive.

---

### Post by Jaygo333 on 2006-01-17
[QUOTE=matthewv]The program has most likely installed itself to ~/.wine/drive_c/Program\ Files/
The drive_c folder created in a hidden folder in your home directory basically acts like your windows c: drive.[/QUOTE]

How do I access this folder and see what's inside. 
I want to be able to run the files inside it?

:h34r: Jaygo333 :h34r:

---

### Post by Turtle.net on 2006-01-17
If you want to access it using nautilus just type Ctrl+l to access the location pop-up. Then type /home/yourlogin/.wine/drive_c
Or just type cd /home/yourlogin/.wine/drive_c in a terminal.
to launch an exe from the commabd line just type wine name.exe (from nautilus you already discovered how to do it ;)
Note : I prefer to use the command line

To play your games have a look to [http://frankscorner.org/index.php]("http://frankscorner.org/index.php")

---

