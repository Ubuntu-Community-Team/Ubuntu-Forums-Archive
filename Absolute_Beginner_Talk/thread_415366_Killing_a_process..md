---
title: "Killing a process."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-04-20
Hey, some times a program locks up in Ubuntu that I can't close down. Is there a function like the Windows "ctrl-alt-delete" to kill a process no matter what.

---

### Post by maxamillion on 2007-04-20
ctrl+alt+esc will turn your cursor into a skull and cross bones, then click on the frozen application and it will kill it (this is called xkill) or you can run top or htop and find the PID and kill it in ther terminal with "kill <pid #>"

---

### Post by Cypher on 2007-04-20
If you can open a Terminal window then do..
```

ps -eaf | grep <program name>

```
This will give you a line with some info, the first number after your username is the PID (process ID). You can use that to send a kill command like:
```

kill -11 <PID>

```
If "-11" doesn't do it, try "-9"..

Regards

---

### Post by Comzee on 2007-04-20
Ok, for some reason the ctrl-alt-esc  flashes black lines on the edge of my screen??
And about the code, 90% of the time I don't know what to type in the terminal.
Exp: To run Wireless Assistant the code was Wlasstant or something like that.

I checked if Xkill was installed and it was, so I don't know about that.

There has to be a simple way to kill a process.

EDIT: Ok I just ran xkill in the terminal and in worked.
```
sudo xkill
```

---

