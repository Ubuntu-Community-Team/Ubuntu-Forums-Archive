---
title: "Change session properties/program order from terminal?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by reeboblue on 2007-06-25
Hi All,

I need to know if there's a way to change session properties, more specifically program order from the terminal?  Just to give some background.  I installed "screenlets" to have OS X style widgets on my desktop.  I also added the Screenlets Daemon to the startup programs using "screenletsd start" as the command.  After adding it to my startup programs, it still was not launching autmatically so I changed the "order" of the screenlets program from the default 50 to something like 40.  Ever since then, my computer just freezes at the splash screen when I login. 

I believe that I need to login through a fail-safe terminal and manually change the "order" value for the screenlets program back to some higher value so that I can login normally.  Does anyone know what configuration file stores the setting for a startup program's order?  I am pretty comfortable with the terminal, but I just don't know where to go to "fix" my issue.  Not sure if this complicates things, but I am running a custom session with Beryl.  If anyone can point me in the right directions, I would greatly appreciate it!!!

Cheers,
-Reebo

---

### Post by gasolino_ on 2007-08-07
I think you resolved after 12 days, anyway in this case the clean way is to delete/rename: ```
~/.gnome2/session
``` This way you have a "clean" session, and the saved is erased. To change the order I think you can try to modify that file. Or if you have added additional startup programs they will be in: ```
~/.config/autostart
``` each entry with his named file.

---

### Post by soulbreak on 2007-08-31
I'm having the same startup problem and I don't have a session file under /.gnome2/ and a /.config/ directory doesn't even exist...


I'm searching for those directories under /home/user/

---

### Post by schorsch on 2007-08-31
What is the output of
```
id
ls -la ~/.gnome2
```

---

### Post by soulbreak on 2007-08-31
I figured it out, I was typing "cd /.config" instead of just "cd .config" noob mistake, go figure problem solved.  TY for the quick response though =D

---

