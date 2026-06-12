---
title: "[SOLVED] Where did it go?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by rock11 on 2007-12-07
Hello guys,
I believe this has happened before,but i don't remember clearly the case,
Here is what happened:
I wanted to install a game,"Risk" on my computer.I typed[FONT="Verdana"]sudo aptitude install xfrisk[/FONT] in the terminal.I do have it now,but how can i start it?
Can't find it at usr/bin directory,nor can i start it trough the Run application menu.One check in the Synaptic Package Manager would show me,that i have the package xfrisk.
I do not insist on the game,still i am bothered with my lack of knowledge.
Thanks:)

---

### Post by cerealtx on 2007-12-07
alt+f2 then type in xfrisk ;)

---

### Post by rock11 on 2007-12-08
> **cerealtx said:**
> alt+f2 then type in xfrisk ;)
I've been trying this.I explained above it didnt work also trough the Run application menu(which is alt+f2).
Other ideas?

---

### Post by spai on 2007-12-08
man xfrisk returns the following:

NAME
       xfrisk - risk board-game client for X11

SYNOPSIS
**       xfrisk <server> [options]**

DESCRIPTION
       This manual page documents briefly the xfrisk program.

       xfrisk  is  a client for connecting to the friskserver.  From there you
       can add players and start a game of risk.

       xfrisk <server> [options]

So you cant just type xfrisk i think, probably you will have to add servers as well.
Hope that helps :)

---

### Post by jimbean on 2007-12-08
just looked in usr games folder found risk icon clicked it and it pop`d up

---

### Post by spai on 2007-12-08
ya i typed ¨risk¨ instead of ¨frisk¨ in the terminal, and it popped up :)

---

### Post by rock11 on 2007-12-08
> **spai said:**
> ya i typed ¨risk¨ instead of ¨frisk¨ in the terminal, and it popped up :)

Yes,that helped.
I typed as well risk at the terminal and it started .
Thanks for the help:)
Cheers

---

### Post by spai on 2007-12-08
No problem, glad to help :)

---

