---
title: "Kubuntu power management"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by cainofnod on 2006-12-18
Greetings,

I just installed Kubuntu and am very pleased. There is a few problems, this one should be the simplest for an experienced operator to solve.  How do I get information pertaining to power management via the bash shell (Command Line) in Kuibuntu?  Powersaved is not installed, I do have guidance-power-manager.py running when I use the ps command.
  The specific information I wish to glean from the shell is this: Battery level, CPU Freq. rough idea about how long until my battery dies. 

I am running edgy:
2.6.17-10-generic #2 SMP i686 GNU/Linux

Thank-you in advance.

---

### Post by benuski on 2006-12-18
For power information, did you try the 
```
acpi
```
command from the command line?

---

### Post by kd7swh on 2006-12-18
acpi is what i use but check out this

[https://wiki.kubuntu.org/KubuntuPowerManagement](https://wiki.kubuntu.org/KubuntuPowerManagement) 

it may help you  understand Kubuntu Power Management.

---

### Post by cainofnod on 2006-12-18
Thanks!  acpi shows battery information and that is exactly what I needed.

---

