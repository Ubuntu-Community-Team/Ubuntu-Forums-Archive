---
title: "more fun with permissions"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-15
Everything I download and run for the first time is not working correctly until I change the permissions. For example, I am trying to run a worms clone and I type './woprc'. This should launch the game but instead, I get something like this:

./woprc: line 24: mode: command not found 

It displays this for about six different named objects (functions or subroutines I'm guessing). Anyhow, the screen clears and a box says that the program abended because it couldn't find the directory. Even though I gave the directory permission 775 and have even tried using sudo to launch the program from the directory containing the program...:confused: How can I get this program working and solve my permission problems...?

later...

---

### Post by taurus on 2006-11-15
Is woprc a script file?  What does line 24 say anyway?

---

### Post by Ben Sprinkle on 2006-11-15
Read the documentation for FAQ's.

---

### Post by saintj0n on 2006-11-15
Here are the offending lines in the program:

line 24: mode = client
line 29: gamemode = deathmatch
line 33: data = ./data
line 44: width = 1000
line 50: height = 1000
line 63: theme = sparse1
line 74: quiet = no
line 80: name = "The Dude"
line 89: color = 255, 255, 255
line 96: team = 0
line 102: keyboard = US
line 107: nballs = 2
line 112: ngoals = 2
line 117: szprob = 0.01
line 122: debug = no
The result is the same each time: command not found
btw: I got to this point by typing 'make'. When I type ./configure, I get "no such file or directory"

---

### Post by taurus on 2006-11-15
```
ls -la
```

---

### Post by saintj0n on 2006-11-15
QUOTE=taurus;1761522]```
ls -la
```[/QUOTE]

Ok..Here is a snapshot of the results

---

### Post by taurus on 2006-11-15
What does the README have to say anyway?  I see there is a Makefile so chances are you need to run "make" at the prompt.  And of course, you need to install "build-essential" first before you can run make...

---

### Post by David_T on 2006-11-15
OK, so that woprc file?  That's a config file, not an executable in the first place.  What you probably have is the source archive, so you need to basically run make while in the main directory.  It looks like it uses SDL, so you might need to apt-get SDL and some other things first.

---

### Post by saintj0n on 2006-11-16
Actually, I downloaded an identical program called wormux. It was located in the repository all along. Whoever put together the program I've been trying to compile needs to document their programs better. The README file had pretty much no useful info in it. IMHO, things like this are the reason why more people don't migrate to linux. If you spend more time putting the game together than playing it, it doesn't take long for the novely to wear off.....

---

