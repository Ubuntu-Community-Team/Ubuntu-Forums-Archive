---
title: "Can't find newly installed program"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by kennm on 2007-04-14
Okay, I got Ubuntu installed, then installed a new program called Stellarium ... I expected it to be added to the K menu somewhere, but I can't find it ... where is it?  where do I look?

all help appreciated ... I get around okay in Windows and even Debian servers, but I'm having trouble grasping some things about Linux GUIs.

thanks 

Kenn

---

### Post by TheRingmaster on 2007-04-14
open the konsole and type the name of the program in there. It should come up as normal. I am not running kde right now so I can't tell you how to add it to the menu.

---

### Post by Maestro23 on 2007-04-14
In terminal you can use the commands locate and whereis to find the bin file to a program.

Ex: locate mplayer or whereis mplayer.

---

### Post by OU812 on 2007-04-14
It sounds like you have to add the entry manually. Once you found the location using the previous posts, right-click anywhere on the menu and you should get another list of options, one of which should be the menu editor.

john

---

### Post by forrestcupp on 2007-04-14
Usually when you install something, the executable bin file can be found in the /usr/bin directory.  If it is a game, it's likely to be found in /usr/games

---

