---
title: "So, I've installed some documentation out of Synaptic..."
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by MonsterBox on 2005-12-07
Um, where did it go?

I downloaded some Python information (a -doc and some other things listed as documentation for learning the language) because I'm really interested in learning how to program stuff for Linux.

However! I cannot figure out where the heck it went. I looked in the terminal turn-arrow after it said it was done, but I saw nothing resembling a path as to where it might have put it. Additionally, I have no idea how to search the file structure. (It's been a decade or more since I used Unix commands. :eek: )

Anyway, any help that might be offered would be much **much** appreciated.

Thanks for reading. :)

---

### Post by aysiu on 2005-12-07
God knows how anyone was supposed to find it, but it's in /usr/share/doc/python2.1-doc/html

---

### Post by matthew on 2005-12-07
Almost any time documentation is installed using apt-get or synaptic it goes to /usr/share/doc/* (where * is a folder based on the program's name). It's not an absolute, but it is pretty standard.

---

### Post by aysiu on 2005-12-07
Good to know.
Didn't know that before.

---

### Post by 23meg on 2005-12-07
[QUOTE=aysiu]God knows how anyone was supposed to find it[/QUOTE]No matter if it's documentation or an application, if you want to know where exactly the files from a certain installed package are, you can right click the package name in Synaptic, hit properties and go to the "Installed Files" tab.

---

### Post by aysiu on 2005-12-07
Good to know. Thanks for all the tips.

---

### Post by equal on 2005-12-07
To continue on this though, I just installed GnuChess and GnuChess book. I can't find them anywhere, they aren't in my applications list. Help? I found GnuChess in my /usr/games, but of course I can't just double-click. Help?

---

### Post by aysiu on 2005-12-07
Alt-F2 ```
gnuchess
```

Does it work?

---

### Post by equal on 2005-12-07
sigh, no. The tool doesn't seem to find it. It's weird. Synaptic Package Manager says I have it, I'm able to find it in my /usr/games directory. I WANNA PLAY CHESS DAMMIT! hahaha.

---

### Post by aysiu on 2005-12-07
[QUOTE=equal]sigh, no. The tool doesn't seem to find it. It's weird. Synaptic Package Manager says I have it, I'm able to find it in my /usr/games directory. I WANNA PLAY CHESS DAMMIT! hahaha.[/QUOTE] Apparently, it needs to be run in conjunction with another application: >        On Debian GNU/Linux  systems  you  can  find  the  documentation  under
       /usr/share/doc/gnuchess/MANUAL.gz which was originally named doc/README
       in the upstream source.  Usually you will want to use gnuchess  through
       a chess interface such as **xboard, eboard** or **gnome-chess**.


---

### Post by equal on 2005-12-08
Thanks! That did it. One last question, I removed a few progs, and their icons are still in the Applications list. How do i get rid of that?

---

### Post by aysiu on 2005-12-08
[QUOTE=equal]Thanks! That did it. One last question, I removed a few progs, and their icons are still in the Applications list. How do i get rid of that?[/QUOTE] Applications > System Tools > Applications Menu Editor

---

### Post by equal on 2005-12-08
You guys rock. Thanks so much!

---

### Post by MonsterBox on 2005-12-08
Thanks for all of your help guys, I really appreciate it.

:cool:

---

