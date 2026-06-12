---
title: "Is there a terminal command = CTRL-ALT-F1?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by cogadh on 2007-07-05
I'm trying to automate some tasks in Ubuntu through some basic scripts and I need to be able to close a current GUI session and get down to the console. Is there a terminal command that can do the same thing as hitting the key combo CTRL-ALT-F1?

---

### Post by Raineer on 2007-07-05
The problem is that Ctrl-Alt-F1 doesn't actually "close" the GUI, it just changes away from it.

If you really need to run a script that requires no GUI, you'll have to lead with 
```
/etc/init.d/gdm stop
``` (or kdm if you run kde)
You'll need root access to the script though, as that's a sudo function normally

edit: I'm curious, what kind of script would you run that requires the GUI to be closed?

---

### Post by cogadh on 2007-07-05
I use a simple script to launch Wine games from the console in their own seperate X session with no window manager. I currently manually do the CTRL-ALT-F1, then log in at the console and run the script, which does the gdm stop function for me before launching the game. I was trying to come up with a less cumbersome way to do it, and I thought it would be bad to run the gdm stop from within the running GUI. If it isn't, then my work is already done and I can use the scripts I already have. If it is bad to do that, then I still need to find a way to automate the CTRL-ALT-F1 function.

On a side note, do you know if there is a way for a script to monitor a running process and execute a command once that process has finished? It would be really cool if I could automate the post-gaming "gdm start" process

---

### Post by cogadh on 2007-07-06
No other ideas?

---

### Post by Nekiruhs on 2007-07-06
This would be useful for me as well. I run F@H on tty1 and would like it just to autostart. 
BTW, can you even run games w/o X?

---

### Post by MoxJet on 2007-07-06
Do you mean you should start the script, running from the x server, terminate the x server, start a new one with only the wine application? 
You could start two separate x servers, the first (host) one still running. Refer to the Xserver manpage.
I guess you could do some tweaking to start x as user, instead of running gdm as root, as I presume Ubuntu does. Then you can kill the x process by the script because it runs on the same user.

Good luck, write back when you solve it!

Nekiruhs, the only games you would be able to run without x is games that does not require x, like command games like MUDs.

---

### Post by Nekiruhs on 2007-07-06
Darn... That would improve perfomance a lot though.

---

### Post by cogadh on 2007-07-06
Perhaps I need to explain more.

I am running Windows games through Wine. I use a script to launch those games in a separate X session without a window manager (i.e. no Gnome or KDE). The window managers can sometimes get in the way when the game is trying to take over the whole screen and it is not really needed to run the game anyway. 

Currently when I do this from the GUI, the games take a performance hit, since the GUI is technically still running on it's own X session. So I changed methods and went with switching to the console with CTRL-ALT-F1, killing the GDM, then launching the script that starts a new X session and the game. This process is a little cumbersome but the performance improvement is fantastic. 

I have since altered the script so that the GDM stop is part of the script, so I was able to remove one step out of the process, but my ultimate goal is to remove nearly all of the manual steps out of the process. I would like to be able to:
[LIST=1]
[*]Launch a script from the GUI that does the CTRL-ALT-F1 function and adds my game launching script to the login scripts (rc.local?)
[*]Log in to the console and have my game script launch automatically
[*]Have the game script monitor the game's executable, so that when it stops running, it will modify the login script to remove the game script and then run "GDM start" 
[/LIST]
Technically, the login script modification can occur before the game finishes, but the GDM start cannot. I suppose I could just have the script wait for a response from me before taking the post-game actions, rather than monitor the executable, but I am also trying to do this for the challenge of it. :)

---

### Post by cogadh on 2007-07-07
No ideas on how to do the CTRL-ALT-F1 from the terminal? I don't need answers for the rest of the script (I'll figure it out), I'm just stumped on the whole CTRL-ALT-F1 thing.

---

