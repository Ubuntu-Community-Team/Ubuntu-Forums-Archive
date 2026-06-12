---
title: "Dapper and 2 problems i have"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-06-23
Hey, im new to dapper but not ubuntu lol :D i did a dist-upgrade today but now the 2 programs that get the most use from me.. mplayer and amsn.. Dont work!
please help me get these working!

~Lance

---

### Post by Brunellus on 2006-06-23
you'll need to be a bit more specific about "didn't work".  What error messages, if any?

---

### Post by noob_Lance on 2006-06-23
lol sry... yea error messages... None. they just start up and nothin. they crash and dont give me any errors..

~Lance

---

### Post by Brunellus on 2006-06-23
that's not terribly helpful, either.  h'm.

open a terminal.  type the following:

amsn > error.log

then type 

gedit error.log 

and post the contents here.

---

### Post by noob_Lance on 2006-06-23
segmentation fault..

thats all it said

---

### Post by Brunellus on 2006-06-23
ugh.  you have found a bug!

follow the bug reporting directions here:

[http://www.ubuntuforums.org/showthread.php?t=100738](http://www.ubuntuforums.org/showthread.php?t=100738)

---

### Post by nanotube on 2006-06-23
[QUOTE=noob_Lance]Hey, im new to dapper but not ubuntu lol :D i did a dist-upgrade today but now the 2 programs that get the most use from me.. mplayer and amsn.. Dont work!
please help me get these working!

~Lance[/QUOTE]

for mplayer, chances are, the following will fix it:
```
sudo aptitude update
sudo aptitude reinstall mplayer-skins
```

don't know about amsn though...

---

### Post by deadgobby on 2006-06-23
[QUOTE=nanotube]for mplayer, chances are, the following will fix it:
```
sudo aptitude update
sudo aptitude reinstall mplayer-skins
```

don't know about amsn though...[/QUOTE]

 That fix the problem I had with Mplayer after the upgrade. BIG THANKS:mrgreen:

---

### Post by nanotube on 2006-06-23
[QUOTE=deadgobby]That fix the problem I had with Mplayer after the upgrade. BIG THANKS:mrgreen:[/QUOTE]
no prob. i had the same problem, that's how i knew about the fix :)

---

### Post by panurge77 on 2006-06-23
As for amsn segmentation fault, its usually about wish8.5
You may search for a way to link it to wish
Or you may do one of the following:
1- Edit your launcher so that it uses the command 
```
wish8.5 /usr/share/amsn/amsn
```
2- Edit amsn launcher in /usr/bin:
sudo gedit /usr/bin/amsn
and change wish to wish8.5 on one of the first lines

---

### Post by noob_Lance on 2006-06-23
the wish8.5 thing didnt work.. still dosnt work right..

and ill try the mplayer thing now

*edit... it worked... i luv you lol :p

---

