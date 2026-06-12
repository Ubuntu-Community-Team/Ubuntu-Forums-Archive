---
title: "Macro tool"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by xhie on 2006-07-14
I know I already asked this question in another forum but I didn't get an answere at all, I'm sure someone must know and bumping it didnt work heh.

I need a macro tool that remembers keyboard and mouse strokes, does anyone know of one that works in ubuntu?

---

### Post by Kilz on 2006-07-14
> **xhie said:**
> I know I already asked this question in another forum but I didn't get an answere at all, I'm sure someone must know and bumping it didnt work heh.

I need a macro tool that remembers keyboard and mouse strokes, does anyone know of one that works in ubuntu?
xmacro and xmacroplay
From Synaptic
Record / Play keystrokes and mouse movements in X displays
xmacrorec can be used to record mouse and keyboard events on any X11 display.

xmacroplay can be used to playback recorded events or send any other
mouse/keyboard events you choose. It is very handy for scripting an
X display - for example controlling a presentation in mgp or ultrapoint
from a script, network connection...

---

### Post by swhebert on 2007-10-28
Hi all,
Not sure if this thread is dead or not,but will try here first.
New to Ubuntu(finally sick enough of MSFT to do something else) and to programming(cant find my favorite utility in the Linux community).Thanks to the Ubuntu community, i have, after considerable fiddling/learning, got Gutsy running on this Vostro 1700, with wireless, sound, and nvidia.

I have read several "macro" questions which center around recording key/mouse strokes. The utility i used in MSFT would do that, but its real usefulness was that whenever a specific string was typed, typically  .sh<spacepar> (period, your shortcut letters,spacebar), it would check a list to see if that sequence was on the list. If it was, the text Steve Hebert was substituted at the cursor where you were in Win. If not, it stuck with the original keystrokes.

i have started with python, got it running got idle running and learned to "print hello world" and count to ten. At this point, i think this project may go faster if i start in the middle of the process, and write a script/'program that will substitute one set of characters, then try to expand it to give it list checking abilities. 

Questions:
1.This program would have to be"resident in memory" in DOS language. I know it probably cannot work at root level,but am hoping for resident at level 5 or so when gui is running for browser, mail, openoffice, etc. Is this feasable in the LINUX architecture?

2. Is Python the language to be working in? I have read the posts about different tools being suitable to different tasks, so have tried to be as specific as possible.

3.I need an example to start from. I dont even know the command to "send" key strokes to the cursor in python. There seem to be a number of list checking examples when i get to that part of the project. I have checked for repositories for python scripts, but havent found a spot with a  lot of variety..

I assume this project is probably too complex for a newbie,but i will really miss my utility, so i thought i would give it a try.
TIA for your help.
Steve

---

### Post by m.lundalv on 2008-05-25
A late response: swhebert, you seem to be looking for what I would call an "abbreviation expansion" tool rather than a "macro" tool.
I just found one called Autokey at 
[http://sourceforge.net/projects/autokey/]("http://sourceforge.net/projects/autokey/")
Cheers /ML

---

