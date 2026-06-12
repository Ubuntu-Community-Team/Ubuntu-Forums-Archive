---
title: "how do you find out why ubuntu crashes?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by unebaguettesvp on 2007-03-30
i'm new to linux, about a month. i'm using ubuntu edgy eft amd 64 bit architecture and i love it. but i am having a consistent problem and it's getting to be annoying.

if there is one thing that i know will happen for sure is that when i come home at night and turn on my computer, ubuntu will crash on me JUST ONCE after about 3 to 5 minutes of usage. after i hit the reset button, my computer is fine for the rest of the night. i have no idea what causes it. it's not consistent. sometimes it happens when i check my email. sometimes it happens when i use firefox.

the only detail i can give is that the screen goes black for 1 second and then it comes back really scrambled in different colors. sometimes, it just freezes.

i want to fix this. so, i was wondering, is there any way to find out why it crashed? can i look in a log file to see the last thing it was doing? there must be some way to debug this.

thanks for any help. i know its vague but i don't know where else to start.

---

### Post by nixclusive on 2007-03-30
you can check out the logs. After restarting from a crash ```
less /var/log/messages
```
Press the END key it will take you to the bottom of the file. Press '?' a prompt will appear. enter 'restart' and you'll be taken to the first occurence of the word restart from the end. check above that. whatever happened before the restart should be there. and yes the logs are mostly time stamped too!! good luck.

---

### Post by unebaguettesvp on 2007-03-30
thanks for the help!!!

looking through the log file i found that this seems to be the last thing before it freezes/crashes!

Mar 29 21:56:34 philip kernel: [   42.263483] agpgart: Found an AGP 3.0 complian
t device at 0000:00:00.0.
Mar 29 21:56:34 philip kernel: [   42.263500] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
Mar 29 21:56:34 philip kernel: [   42.263556] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
Mar 29 21:56:34 philip kernel: [   42.563581] [drm] Setting GART location based on new memory map
Mar 29 21:56:34 philip kernel: [   42.563592] [drm] Loading R300 Microcode
Mar 29 21:56:34 philip kernel: [   42.563659] [drm] writeback test succeeded in 1 usecs
Mar 29 21:56:50 philip gconfd (philip-4754): starting (version 2.16.0), pid 4754 user 'philip'
Mar 29 21:56:50 philip gconfd (philip-4754): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 29 21:56:50 philip gconfd (philip-4754): Resolved address "xml:readwrite:/home/philip/.gconf" to a writable configuration source at position 1
Mar 29 21:56:50 philip gconfd (philip-4754): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 29 21:56:50 philip gconfd (philip-4754): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 29 21:56:50 philip gconfd (philip-4754): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 29 21:56:55 philip gconfd (philip-4754): Resolved address "xml:readwrite:/home/philip/.gconf" to a writable configuration source at position 0
Mar 29 21:59:37 philip syslogd 1.4.1#18ubuntu6: restart.


i'm not sure what xml:readwrite:/home/phillip/.gconf does? can anybody help please? thanks!

---

### Post by unebaguettesvp on 2007-03-30
can anybody help?

---

### Post by unebaguettesvp on 2007-03-30
so, my computer just restarted again for no reason. i was eating lunch and then i hear the computer shut off RANDOMLY!!! i wasn't even by the computer!

this is really annoying. i checked the messages logfile. this is what it said right before restarting:

Mar 30 11:34:17 philip -- MARK --
Mar 30 11:54:17 philip -- MARK --
Mar 30 12:14:17 philip -- MARK --
Mar 30 12:34:17 philip -- MARK --
Mar 30 12:54:17 philip -- MARK --
Mar 30 13:14:17 philip -- MARK --
Mar 30 13:34:18 philip -- MARK --
Mar 30 13:51:10 philip syslogd 1.4.1#18ubuntu6: restart.

i really want to fix this! my ubuntu install is so unstable. i had better luck with windows. but i'm not switching back! i'm going to make this work.

where do i start?!

could it be because i am using the amd 64 bit version of edgy?

---

### Post by ajaustin on 2007-04-01
are you sure this isn't a hardware problem?

---

