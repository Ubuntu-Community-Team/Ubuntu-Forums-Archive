---
title: "Hacking/Memory editing program?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by joeshmo on 2006-11-02
Hey guys, I recently switched over to ubuntu from windows XP home because windows xp died, I tried to mess around with some files and now winlogon.exe is dead, it gives me bsods even in safe mode. Well, until I get a new XP home cd, I am stuck using ubuntu drapper on a 10 gig partition of my hard drive. I was just wondering if there was a program for ubuntu that allows you to modify memory, like pointers and such. A program like cheatengine or tsearch on windows, and yes, I have tried wine but it will only see the wine processes because it was built in the windows environment and ubuntu uses a different environment for their processes. Basically, what it is is it lets you search through memory with a value, lets say 15. It looks through all of the allocated memory for the process you attached to and find any ones equal to 15, in a 4 byte, 8 byte, float, double or two byte type. Then, you go into the program you've attached to and make that value change, lets say to 16. You go back into the cheat program, search continious/next search for 16, so any values that you found before that were 15 that changed to 16 will show up. Then you can take these adresses you found and add them to a table, there you can freeze them/change their value. Also, cheat engine allows you to debug in the kernel and add breakpoints for ASM code, like changing the EAX at a certain adress, or changing a certain section of memory to nop or ticking ZF at a certain place to change the jump condition (like jne to je and vice versa). So does anyone know of a program that will let me do this? Thank you for your time.

---

### Post by yabbadabbadont on 2006-11-02
gdb

(The GNU Debugger)

---

