---
title: "help with programing"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by bno545 on 2007-09-10
well i don't know if i can even do this but.... i am trying to run two different programs (the timidity midi engine and guitar pro 5). i don't want to open up terminal and start timidity every time i want to use guitar pro 5, so i am trying to use gedit and run the command to start the engine and GP5 at the same time by saving the file as an excitable.  evey time i open the file it will only start the first command. i want to know what the "command/symbol/key/whatever they are called" to go to stop and go the next line.  if this makes any sense please help me!!

thanks

---

### Post by teimu on 2007-09-10
"command1 & command2" might work. notice the ampersand between commands

---

### Post by lambros on 2007-09-10
If you want to put this into a desktop shortcut (Launcher), you'll probably need to use something like this for the launcher's Command:

```
sh -c "command1 & command2"
```

That would give you a shortcut that can run two executable commands, which seems to be what you want.  But beware!  Once you've finished your command2, your command1 may still be running in the background.  So next time you use your shortcut, you might end up with 2 instances of command1 running - not ideal!

Perhaps there's a better way?  If you want something like timidity to run in the background, maybe you could add it to your GNOME session startup commands?

Lambros

---

