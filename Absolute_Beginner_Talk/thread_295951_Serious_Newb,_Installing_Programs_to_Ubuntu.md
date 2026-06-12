---
title: "Serious Newb, Installing Programs to Ubuntu"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by That_Geek on 2006-11-08
well, i run ubuntu and have a dual boot with the doze, and on doze i have an awesome game called Enemy Territory

it is supposed to be able to play on linux without the use of wine

i dled it and it has a .run extension on it, now i dont know what to do with it

lol
anyone know how to install .run files?

---

### Post by o_fortuna on 2006-11-08
Here you go -- it's a bit complicated.

1) Move the file to your desktop. It's easier that way (if it's already there that's fine).

2) Open up a terminal. First click Applications, then Accessories, then click Terminal.

3) When the window appears, try this:
```
cd Desktop
```
Now type (of course, replace whateverthefileiscalled with, you know, whatever the file is called ;))
```
./whateverthefileiscalled.run
```
I think that should work. Whenever you want to run files with .run extensions, put ./ in front of them in the terminal.

edit: Oh, if it gives you an error about not being able to write, put "sudo" in front of it and put your password in when it asks.

---

### Post by That_Geek on 2006-11-08
it isnt working

its saying that 

```
bash: cd: desktop: No such file or directory
```

any idea what i should do?

---

### Post by MasterOfDisaster on 2006-11-08
Capitalize the 'd' in Desktop.  If you are ever stuck for the file or directory name, just type in 'dir' and hit enter.  It will give you the names of everything in your current directory.

---

### Post by aysiu on 2006-11-08
This tutorial is from 2004, so I'm not sure if it's up to date, but you may want to check out [HOW TO: install Enemy Territory](http://ubuntuforums.org/showthread.php?t=5246)

---

### Post by d3v1ant_0n3 on 2006-11-08
> **aysiu said:**
> This tutorial is from 2004, so I'm not sure if it's up to date, but you may want to check out [HOW TO: install Enemy Territory](http://ubuntuforums.org/showthread.php?t=5246)


It's pretty up to date- I installed enemy territory a couple of days ago using the newer file and that howto- all I had to do was switch the file names.

---

### Post by That_Geek on 2006-11-08
> **aysiu said:**
> This tutorial is from 2004, so I'm not sure if it's up to date, but you may want to check out [HOW TO: install Enemy Territory](http://ubuntuforums.org/showthread.php?t=5246)

thanks for that, i got it all installed, but now it wont start

lol

i guess im just gonna use the doze for right now until i feel like messing with it again

---

### Post by That_Geek on 2006-11-09
so, anyone have any ideas what might be wrong?

---

### Post by .t. on 2006-11-09
No-one can help unless you describe your situation better. I've never played the game, so I can't; but I'm sure someone else can.

---

### Post by That_Geek on 2006-11-09
well, sorta fixed the problem

i got the program to start, it just turns out i dont have any drivers installed for my video card, and the game is running really slow

can someone help me install the drivers off my cd?

sorry im such a newb

---

### Post by 3rdalbum on 2006-11-09
This depends on which graphics card you have - is it ATI, or Nvidia?

---

