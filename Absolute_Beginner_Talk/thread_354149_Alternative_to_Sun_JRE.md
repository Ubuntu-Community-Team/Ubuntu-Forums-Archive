---
title: "Alternative to Sun JRE?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2007-02-05
A java-based application I am using is giving me some issues -- like windows hanging up and refusing to close when I try to exit. The windows can still be minimized, but not closed -- even via System Monitor. 

The developer of the software is looking inot the issue, but he also suggested trying a different JRE.

Is this a reasonable suggestion? If so, does anyone have any suggestions on another JRE to try?

---

### Post by tbroderick on 2007-02-08
> **bcdeck said:**
> 
Is this a reasonable suggestion? If so, does anyone have any suggestions on another JRE to try?

You could try Blackdown, but I don't think it would make much difference. What program is giving you trouble? Maybe try a different version # of Sun JRE.

---

### Post by meng on 2007-02-08
In a terminal, type:
java -version

and check which is your default java.

---

### Post by bcdeck on 2007-02-12
My Java version info:

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

the program apparently comes with a JVM -- it's log says it's using VM: 1.5.0_10 / 49.0

---

