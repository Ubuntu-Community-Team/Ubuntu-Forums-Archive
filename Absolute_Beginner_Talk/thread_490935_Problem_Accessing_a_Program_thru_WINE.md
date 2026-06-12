---
title: "Problem Accessing a Program thru WINE"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-07-03
Hi all,

I'm having a bit of an odd problem, and it's one that's hard to summarize in a few keywords, so I'm not finding anything thru searching the forum.

I have several programs I installed through wine. One of them, for example, is the Poker Stars poker room client. It's installed at /home/steve/.wine/drive_c/Program Files/PokerStars, so if I go to the terminal and type

> wine "/home/steve/.wine/drive_c/Program Files/PokerStars/pokerstars.exe"

the client runs. Similarly, the program auto-installed a launcher, and the command is:

> env WINEPREFIX="/home/steve/.wine" wine "C:\Program Files\PokerStars\PokerStars.exe"

So -- that was all just background/comparison.  I have another program called Steel Panthers - World At War installed under Wine. This program is located in "/home/steve/.wine/drive_c/Matrix Games/Steel Panthers World At War" and the executable is MECH.EXE. The installer didn't create a launcher, so I made one myself. For the command I put:

> env WINEPREFIX="/home/steve/.wine" wine "C:\Matrix Games\Steel Panters World At War\MECH.EXE"

And...nothing happened when i double clicked on it. I tried changing the command to look like the Unix filesystem (/home/steve/.wine/drive_c/Matrix Games/Steel Panthers World At War) and no luck.  

Now, when I went to the terminal and typed:

>  wine "/home/steve/.wine/drive_c/Matrix Games/Steel Panthers World At War/MECH.EXE"

it responded with:

> The instruction at 0x0054ec1b referenced memory at 0x00000010.
The memory could not be read.

Same thing happened when I put it in "Windows-like" format.

BUT if I cd my way to the /home/steve/.wine/drive_c/Matrix Games/Steel Panthers World At War/ directory and just enter "wine MECH.EXE" -- the program runs fine (well, I haven't checked all the functionality under WINE, but it launches).

Any ideas as to why this isn't working?

---

### Post by avik on 2007-07-03
The only thing I can think of is that MECH.EXE references other the files it needs in a way that you have to be in the directory to access them.  I don't know the exact details, but it seems to be some fundamental difference between the two exes.

---

### Post by ResumeMan on 2007-07-04
Well I still have no idea what the issue is. But I was able to follow the advice [here]("http://ubuntuforums.org/showthread.php?t=446734&highlight=launcher+browse") to create a script with the cd command and the execute command. So I've got my launcher.

---

