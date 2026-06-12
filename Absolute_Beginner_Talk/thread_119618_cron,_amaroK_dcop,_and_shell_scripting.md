---
title: "cron, amaroK dcop, and shell scripting"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Im_Just_GrayT on 2006-01-19
ive recently switched to ubuntu breezy badger but every night i have had to boot back into windows so i can use my alarm clock. i found a tutorial using crontabs to make an alarm clock but it doesnt seem to be working. 

I have made a shell script that when executed will "press" the play button on amaroK. but when i add it to my crontab entry it doesnt do anything at the selected time (i know about the 24hr clock system). anyone know what im doing wrong?

p.s. I'm sorry if this question doesnt fit in this forum section. I couldnt find one that suited it better.

---

### Post by cwaldbieser on 2006-01-19
[QUOTE=Im_Just_GrayT]ive recently switched to ubuntu breezy badger but every night i have had to boot back into windows so i can use my alarm clock. i found a tutorial using crontabs to make an alarm clock but it doesnt seem to be working. 

I have made a shell script that when executed will "press" the play button on amaroK. but when i add it to my crontab entry it doesnt do anything at the selected time (i know about the 24hr clock system). anyone know what im doing wrong?

p.s. I'm sorry if this question doesnt fit in this forum section. I couldnt find one that suited it better.[/QUOTE]

I am guessing that because your cron script is executing in the back ground and not attached to a terminal or display, it is unable to contact your desktop session via DCOP.

I would try splitting the problem into two parts.  I would have the croj job create a blank file in your home directory  (e.g. "touch ~/.my-alarm").  Then, in your ~/.kde/AutoStart, I would put a script like this:
```

#!/bin/bash
while true; do
   if [ -f ~/.my-alarm ]; then
      #Code to turn on Amarok goes here.
      
      exit
   fi
   sleep 10 #sleep 10 seconds then check again.
done

```

You can make it more sophisticated so you can reset the clock, give it a GUI, etc. but the basic idea is still the same.

---

