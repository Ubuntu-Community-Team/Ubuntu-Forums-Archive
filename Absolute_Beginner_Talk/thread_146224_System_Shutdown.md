---
title: "System Shutdown"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by agent_shooter on 2006-03-17
My system goes into suspend mode and then won't come out.  Is there a way to disable this suspend feature.

I would rather keep it on and then just manually turn my monitor off.

Agent S

---

### Post by rfruth on 2006-03-17
Edit the /etc/default/acpi-support file 

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Suspend_to_memory]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Suspend_to_memory")

---

### Post by agent_shooter on 2006-03-17
Thank you so much for your help.

Agent S

---

### Post by agent_shooter on 2006-03-18
I changed the hiberate=true to hiberate=false but that didn't fix the problem.

Whenever I leave the computer for a long time, is goes into suspend and when I press a key on the keyboard the screen comes back on, I can move my mouse, but I can't close or open any of the programs.  I just get the cursor move in the circle.

Any other ideas?

Thanks
Agent S

---

### Post by rfruth on 2006-03-19
I have a few ideas, hopefully one of um will work for you - anyway have all power conservation options been disabled  in the BIOS and have all ACPI daemons been removed via the package manager (or whatever) also when the computer won't wake can you switch to a different run level (Ctrl-Alt-F2) and login (is the kernel having trouble with sleep or is it the X windows system) ?

---

