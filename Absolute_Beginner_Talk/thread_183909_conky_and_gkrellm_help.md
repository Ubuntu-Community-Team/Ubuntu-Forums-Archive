---
title: "conky and gkrellm help"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by lordharsha on 2006-05-28
I installed conky and ran it thru the terminal, but when I close the terminal, even conky closes. Is there any way to run conky without using the terminal so that it's always open? And how do I get conky (or any other program) to run when I start up?

I also have a doubt about gkrellm. When I run it (by clicking on the icon), it opens in a new transparent window, and I can see a tab for it in the panel. Is there any way to avoid this?

---

### Post by johnc4510 on 2006-05-28
System>Preferences>Sessions
click on startup programs
click on add
type in conky
This will launch conky at startup. You can use this for any app you want to run at start, however administrative apps need gksudo in front of the app name.

gkrellm: once it launches, right click on the title bar and reconfigure to your liking

---

### Post by lordharsha on 2006-05-28
thanks

---

### Post by uzi09 on 2006-05-29
just for the record, if you run a program from the terminal by just calling its name, the prompt wont return until you close that program, and if you were to close the terminal, it'd close the program too (as you experienced with conky).

there are 2 ways to start programs and get your prompt back so you can continue to open other programs or do w/e u want at the prompt (even close the terminal) and still have the program running in the background.

1) basically, you start the program like normal, BUT BEFORE YOU HIT ENTER, and an ampersand (&) at the end of it. this will "background" the task. with some programs, they may not show a prompt again, but you could close the terminal if you wanted and the program would still run. if you want to get the prompt back, you can just type:
```
 bg
```
and hit enter, and it'll bring the prompt back up.

2) you can start the program like normal (without the ampersand, & <~ this thing) and what you can then do is suspend the task by pressing:
Control+z
then you'll get a prompt up and the program will freeze/pause until you bring it back up front, or send it to the background.
to bring it back up front, you just type:
fg
and hit enter.
if you want the prompt to come back again, and the program to continue in the background, just type:
bg
and hit enter and you're good to close the terminal/use the prompt.

---

