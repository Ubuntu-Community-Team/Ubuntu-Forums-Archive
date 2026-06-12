---
title: "Applications list for killall?"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by edwina on 2005-08-07
A short, noob question ...

If I have to close an application (Beep media crashes whenever I press "play", for example), then I can open a terminal and type "killall <application name>", yes?

There must be a way, then, to get a list of all the running applications. Otherwise I have to remember, for example, "beep-media-player" and the tab-autocomplete doesn't seem to work for applications. 

Can anyone tell me the command, please?

---

### Post by dave9191 on 2005-08-07
ps -A

that will list all the running processes on your system. You can then kill a process by reading off its id and typing 

kill <ID>

Or killall <app name>. Or pkill <Regular Expression>

pkill media will kill every application with the word media in the title. Auto completion will not work for application names.

And in kde pressing Ctrl + Esc will bring up a graphical task list from which you can click to choose. I do not believe that this was implemented in gnome yet. 

Dave

---

### Post by N'Jal on 2005-08-07
Or use top, 

type top in the command prompt, to kill a process type k it will ask for the processes pid number, this is the column of number's on the left, it'll then ask for the PR number type that in and most of the time it works.

---

### Post by az on 2005-08-07
You can use the system monitor applet.  When you click on it you get a list of running processes and their ressource usage.  You can list it in descending order of cpu useage and kill the runaway process...

---

### Post by wellery on 2005-08-08
you can also use xkill and then click on the application window that you wish to kill.

---

### Post by jobezone on 2005-08-08
[QUOTE=edwina]A short, noob question ...

If I have to close an application (Beep media crashes whenever I press "play", for example), then I can open a terminal and type "killall <application name>", yes?

There must be a way, then, to get a list of all the running applications. Otherwise I have to remember, for example, "beep-media-player" and the tab-autocomplete doesn't seem to work for applications. 

Can anyone tell me the command, please?[/QUOTE]
 I usually use
```
ps aux
```
for a full view of processes and user which own them

---

### Post by AlexDe on 2005-08-08
I usually use 

```
ps aux | grep appname
```

---

### Post by edwina on 2005-08-09
That should do it! Thank-you all.

---

### Post by trash on 2005-08-09
I'm surprised nobody uses the force quit applet, i love that thing:)

---

