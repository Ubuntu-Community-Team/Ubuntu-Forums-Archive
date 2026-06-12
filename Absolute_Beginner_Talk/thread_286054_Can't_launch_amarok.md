---
title: "Can't launch amarok"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by larryni on 2006-10-27
I have problems launching amarok. I think I know partly what happened, but can't get it fixed now. 

I'm just did a clean install of 6.10. Last night I wrote a script to backup the mysql amarok database, named it 'amarok' and saved it in ~/bin.

Earlier before the install I made sure everything was backed up, including my bin folder. After re-installing Ubuntu and my backups I installed all my apps. When I tried to launch the amarok from the menu I just got some short disk activity and then nothing. Suddenly it dawned on me that I was running the script each time instead of the app. I renamed it to something else, tried to launch amarok again, got the wizard and that was it - amarok just disappeared. All I get now is the splash screen when I try to launch it. I have tried completely removing and re-installing it but it still doesn't go any further than the splash screen.

Any ideas what's happening here?

---

### Post by larryni on 2006-10-27
I just tried to launch it from the console and here is what it spits out
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...

```

---

### Post by larryni on 2006-10-28
Still no luck getting amarok running. I've been trying to find out what 'input device 168' is, but can't find it. Any help greatly appreciated.

---

### Post by larryni on 2006-10-28
Solved.

Looks like it was a problem with MySQL. After deleting the amarok config file and selecting SQLite it started up. Then it let me switch to MySQL.

---

