---
title: "synaptic error"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Corey4666 on 2006-07-19
whenever i open synaptic i get this "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
i dunno what to do now i typed "dpkg --configure -a" into the terminal and it said "dpkg: requested operation requires superuser privilege"

also i need to know something is there a process manager thing just like windows? cuz in windows you can press CNTRL+ALT+DEL and it will open process'es cuz i need to kill synaptic cuz it still runs in the background or something and i cant open other things like update manager or whatever its called cuz it says some other application of the same type is running

---

### Post by Kilz on 2006-07-19
> **Corey4666 said:**
> whenever i open synaptic i get this "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
i dunno what to do now i typed "dpkg --configure -a" into the terminal and it said "dpkg: requested operation requires superuser privilege"

also i need to know something is there a process manager thing just like windows? cuz in windows you can press CNTRL+ALT+DEL and it will open process'es cuz i need to kill synaptic cuz it still runs in the background or something and i cant open other things like update manager or whatever its called cuz it says some other application of the same type is running

Type
```
sudo dpkg --configure -a
``` into the terminal.

---

### Post by Corey4666 on 2006-07-19
why did you quote me? lol thanks for the help it all works now 

does anyone still know about a process manager? :confused:

---

### Post by Chemroydal Tissue on 2006-07-19
I believe you want System->Administration->System Monitor, then click the Processes tab.

---

### Post by Klemik on 2006-07-19
> **Corey4666 said:**
> why did you quote me? lol thanks for the help it all works now 

does anyone still know about a process manager? :confused:

Download automatix. It has option to configure it, I dunno how to make it manually.

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by Kilz on 2006-07-19
> **Corey4666 said:**
> why did you quote me? lol thanks for the help it all works now 

does anyone still know about a process manager? :confused:

Just habbit, I always quote who I reply to. It may not matter with 2 posts, but in longer threads it avoids confusion.

[quote=Klemik]Download automatix. It has option to configure it, I dunno how to make it manually.

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)[/quote]
Sometimes Automatrix gets errors to. If you dont know what it did, or it did it so fast you couldnt see the error, it can be hard to fix.
If you are setting up a lot of applications , it may be ok. But for one or two things you may be better off installing it yourself. 
You will also learn a lot more, that way when you find an application you want that isnt in automatrix you know how to install it.

---

### Post by Corey4666 on 2006-07-19
ok thanks everyone i got all the info i needed

---

### Post by cstudent on 2006-07-19
This is the code from the Automatix script that enables Ctrl-Alt-Del to open System Monitor

```

 gconftool-2 -t str --set apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete" && gconftool-2 -t str --set /apps/metacity/keybinding$

```

---

