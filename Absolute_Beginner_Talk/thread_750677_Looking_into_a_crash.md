---
title: "Looking into a crash"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by cisforcojo on 2008-04-09
I've just had my first hardcore linux crash. I leave my computer on every night (usually downloading something) and when I got up this morning, X appeared to be shutdown (it was at the normal tty1 login screen 'login: ') and was saying something about a SysRq crash. I was still a little groggy and as soon as I hit a button to start typing my username, my computer turned off. It's probably nothing, but I err on the side of paranoia. How can I check my system logs to know what exactly happened? I've checked /var/log/messages and strangely, there appears to be no gap in time (and also nothing useful from a quick check)

I just read about a denial-of-service attack that hackers can use to exploit sysrq so I'm a little paranoid. Any help on how to look into it would be greatly appreciated!

EDIT: Found it. Any ideas on what this could be?
```
Apr 10 02:05:48 tipping-point kernel: [16671.408000] SysRq : Trigger a crashdump
Apr 10 02:05:48 tipping-point kernel: [16671.408000] SysRq : Changing Loglevel
Apr 10 02:05:48 tipping-point kernel: [16671.408000] Loglevel set to 8
Apr 10 02:05:48 tipping-point kernel: [16671.408000] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks 
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Unknown key released (translated set 2, code 0x74 on isa0060/serio0).
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Use 'setkeycodes 74 <keycode>' to make it known.
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Unknown key released (translated set 2, code 0x74 on isa0060/serio0).
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Use 'setkeycodes 74 <keycode>' to make it known.
Apr 10 02:05:48 tipping-point kernel: [16671.408000] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks 
Apr 10 02:05:48 tipping-point kernel: [16671.408000] SysRq : Changing Loglevel
Apr 10 02:05:48 tipping-point kernel: [16671.408000] Loglevel set to 2
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Unknown key released (translated set 2, code 0x65 on isa0060/serio0).
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Use 'setkeycodes 65 <keycode>' to make it known.
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Unknown key released (translated set 2, code 0x74 on isa0060/serio0).
Apr 10 02:05:48 tipping-point kernel: [16671.408000] atkbd.c: Use 'setkeycodes 74 <keycode>' to make it known.
Apr 10 02:05:48 tipping-point kernel: [16671.408000] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks 
Apr 10 02:05:48 tipping-point kernel: [16671.412000] atkbd.c: Unknown key pressed (translated set 2, code 0x75 on isa0060/serio0).
Apr 10 02:05:48 tipping-point kernel: [16671.412000] atkbd.c: Use 'setkeycodes 75 <keycode>' to make it known.
```

---

### Post by Rocket2DMn on 2008-04-09
That's kind of strange.  That output looks like some sort of I/O error, probably with your keyboard.
You can also check messages.0 and dmesg.0 and syslog.0 or older for more information (these should be from the previous run time I think, e.g. before you restarted the computer).
Hardware crashes are notoriously difficult to track down.  I wouldn't really sweat it unless it happens again.
If you are behind a router and don't have ports forwarded and open on your computer, you should be pretty safe from hackers.

---

### Post by cisforcojo on 2008-04-10
I do have ports forwarded but only for torrents (50001 - 50008)
I'll try running nessus on myself

---

### Post by Rocket2DMn on 2008-04-10
OK don't stress it too much.  If it happens again, jump on the logs ASAP to see if you can find anything, otherwise it becomes more difficult to track down the problem as time passes.  Then just post anything back to this thread and I'll have a look - I'm subscribed to the thread so I will see any updates, even if it's a few days/weeks/etc from now.

---

