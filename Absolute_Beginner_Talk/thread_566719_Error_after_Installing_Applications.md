---
title: "Error after Installing Applications"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by khoda on 2007-10-03
I get this error after installing an application and opening it by typing the name in the terminal. Here's an example after I installed kcalc:

xxx$: kcalc
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by Paul820 on 2007-10-03
Is it not in the menu? Have you tried pressing ALT+f2 to run it?

---

### Post by khoda on 2007-10-03
Ooops, my apologies for the ambiguity. 

The program runs fine, but I get that error as well. What is that error?

---

### Post by ThrobbingBrain66 on 2007-10-03
> **khoda said:**
> I get this error after installing an application and opening it by typing the name in the terminal. Here's an example after I installed kcalc:

xxx$: kcalc
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Read the following thread:
[http://ubuntuforums.org/showthread.php?t=557158](http://ubuntuforums.org/showthread.php?t=557158)

To edit the file (assuming you're using Kubuntu)
```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by Hospadar on 2007-10-03
I think the issue here is that sometimes your X file has extra devices in it that don't actually exist.  So you shouldn't worry about these kinds of errors.  If you can't use your nonexistant joystick in kcalc it's not the end of the world i suspect =)

---

