---
title: "kill process"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-18
Hey!

How can i kill a process if some full screen app freezes completely and i cant reach desktop. I mean something like ctrl alt delete in wins?

Thanks

---

### Post by Fataltragedy2 on 2007-03-18
Type xkill in terminal. Your cursor will change to cross bones and a skull. Click the window you want to close.

---

### Post by Vandorius on 2007-03-18
How can i open the terminal if everithning froze and im in full screen app?

---

### Post by 23meg on 2007-03-18
You can switch to a virtual terminal with Ctrl + Alt + F1, but xkill won't work there. Instead, you can use kill, killall, pkill etc.

---

### Post by AtrejuT on 2007-03-18
you should be able to press Ctrl+Alt+F1 to get to a terminal.
there run either 
```

sudo killall *programmname*

```
or 
```

ps -aux
kill *process ID*

```
where you get the process ID from the command ps-aux (just look for the right programme)

---

### Post by oilchangeguy on 2007-03-18
you can also go to applications, accessories, terminal. right click on terminal, and select, add this launcher to panel. so as long as your cursor will move you'll have access to the terminal.

---

### Post by Vandorius on 2007-03-18
How do i get back the GUI after that?

---

### Post by 67GTA on 2007-03-18
You could try adding the FORCE QUIT applet to yur panel. It will let you kill any program that has frozen. Right click panel>add to panel>force quit> then click add.

---

### Post by Vandorius on 2007-03-18
I looked here but i dont have any force quit. But i think f1 and kill process will do if i only know how to get back to GUI then.

---

### Post by 67GTA on 2007-03-18
What version are you running? Ubuntu or Kubuntu?

---

### Post by Vandorius on 2007-03-18
Im runing Ubuntu 6.10

---

### Post by 67GTA on 2007-03-18
The Force Quit applet should be there. Just right click on your panel (system tray), click on "add to panel", look under "desktop and windows" and there should be a force quit applet. Then click on it and click "add" at the bottom of the window.

---

### Post by Obor on 2007-03-18
> **Vandorius said:**
>  i think f1 and kill process will do if i only know how to get back to GUI then.

Ctr+Alt+F7

---

### Post by Lord Illidan on 2007-03-18
You could also install htop from the repos. It is similar to top but it can actually kill processes too..and is console based.

---

### Post by fastwrite on 2008-03-30
If you want to force a restart of your GUI, you can press CTRL+ALT+BACKSPACE - it then forces the X to restart, and not a total restart.

---

