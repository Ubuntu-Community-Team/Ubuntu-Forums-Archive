---
title: "[SOLVED] command line terminal command needed"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by wana10 on 2007-09-13
hi, quick question. what would be a one line command to launch a terminal window and then run a command from inside that terminal.
i have copied the radio program from september desktop thread(awesome, i suggest you try it) and want to launch it from my fluxbox menu. 
the program is at /home/name/.radio
i use gnome-terminal

any help greatly appreciated, thank for your time

---

### Post by CaptainInsaneO on 2007-09-13
I'm not really sure what you want to do. Are you trying to create a launcher? I know you said you want to launch a terminal and auto-start a command from that terminal, but that seems like you're going through your butt to get to your elbow when you could just make a launcher. :confused:

---

### Post by mcduck on 2007-09-13
```
gnome-terminal -x command
```

For example, I use 'gnome-terminal -x ncmpc' to launch my absolute favourite music player from a panel launcher.

So, for your case the command would be "gnome-terminal -x  /home/name/.radio"

---

### Post by wana10 on 2007-09-13
@mcduck: works perfectly, thank a million!

@captaininsane0: i could make a launcher, yes, but where would i put it? i'm running fluxbox with no desktop icons and no panels, everything is through the alt+f2 launcher and the right click menu.

---

### Post by CaptainInsaneO on 2007-09-13
Right, right I see what you mean. Sorry for the confusion! ](*,)

---

### Post by mdpalow on 2007-12-18
> **mcduck said:**
> ```
gnome-terminal -x command
```

For example, I use 'gnome-terminal -x ncmpc' to launch my absolute favourite music player from a panel launcher.

So, for your case the command would be "gnome-terminal -x  /home/name/.radio"

gnome-terminal -x command    

good one..

---

