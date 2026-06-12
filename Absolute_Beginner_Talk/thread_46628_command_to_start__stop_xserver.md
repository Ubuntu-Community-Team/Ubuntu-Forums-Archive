---
title: "command to start / stop xserver?"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-05
my god! Why is it so damn difficult to find out a simple command? I just want to know how to start xserver from the command line and 20 mins of searching these forums and google has not given me an answer.

---

### Post by apollyonis on 2005-07-05
If I rebemeber correctly, GDM replaces what the xserver is. Do ```
man gdm
``` 
I don't remember if the commands were gdmstop, gdmstart, and gdmrestart for restart. Of course, you could do a sudo killall gdm and sudo gdm to restart the xserver.

---

### Post by gammyhand on 2005-07-05
[QUOTE=apollyonis]If I rebemeber correctly, GDM replaces what the xserver is. Do ```
man gdm
``` 
I don't remember if the commands were gdmstop, gdmstart, and gdmrestart for restart. Of course, you could do a sudo killall gdm and sudo gdm to restart the xserver.[/QUOTE]
 Thanks :)

---

