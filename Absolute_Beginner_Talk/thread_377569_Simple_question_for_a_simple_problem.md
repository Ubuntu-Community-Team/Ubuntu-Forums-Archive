---
title: "Simple question for a simple problem"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-03-06
I've got beryl rocking my laptop, it's quite nice.  The problem is that every once in a while, when I boot my laptop, beryl doesn't start.  The solution is simple enough, open terminal, type beryl, and SHAZAM! back to beautiful desktop.  My question is, how do i run beryl in terminal so I can then close the terminal window and keep beryl running.  Currently, when I close the terminal in which I typed beryl, beryl stops, thinks go all wierd and I usually have to restart.  I know there is something really simple, liking beryl -s, or something similar.  Thanks for the help gang.

---

### Post by bernied on 2007-03-06
Use the '&' at the end of the line:
```
beryl &
```This starts the process in the background and you can close the terminal. 
Usually when people say a problem is simple they are wrong.

---

### Post by bernied on 2007-03-06
Incidentally, the same thing happens on my laptop, so I use a script that first starts beryl-manager, then waits for 5 seconds, then starts beryl, something like this:
```
#!/bin/bash
beryl-manager &
sleep 5
beryl &
```This might not be quite right, I don't have it with me.
The first line says 'I am a script to be run by the program /bin/bash' and the sleep command is the thing that seems to fix the sometimes starts, sometimes doesn't problem.

 You can save this as a text file, make sure it's executable, then run it. You can even put it (or link to it) in ~/.kde/Autostart and it will start automatically. But you might want to disable the built-in autostart first, but I don't know how that works - is it in a menu somewhere?

---

### Post by xboxbman on 2007-03-06
> **bernied said:**
> Use the '&' at the end of the line:
```
beryl &
```This starts the process in the background and you can close the terminal. 
Usually when people say a problem is simple they are wrong.


```
 beryl &
``` isn't working. it still shuts down beryl when I close the terminal window., beryl is having real trouble working on start up lately.  It starting to lose it's coolness.

---

### Post by bernied on 2007-03-06
Beryl is cool, it's just still in development.
I don't use it either, hence the script. I just turn it on with a click on that script when I want to impress people with how cool linux can be. I find it very flaky and hungry for power, but still bloody brilliant.

So I was wrong after all, it wasn't simple...
sorry

---

### Post by kynikos on 2007-03-06
I'm rather new to Ubuntu myself, so forgive me if I've misinterpreted the problem.

Instead of trying to start beryl from the terminal window, press Alt-F2 to bring up the Run Application window. Type "beryl" (without quotation marks) and press Run. Hope this helps.

-kynikos

---

