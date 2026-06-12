---
title: "Add/Remove Applications Broken Packages"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by trginter on 2007-06-19
Just installed Ubuntu a few hours ago, so I'm pretty new at this...

I just tried to access the Add/Remove Applications menu and I get this error...

> 
Failed to check for installed and available applications


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Any ideas how to fix this?

---

### Post by kagashe on 2007-06-19
Please post the contents of the file "/etc/apt/sources.list".

kagashe

---

### Post by zanglang on 2007-06-19
Try copy and pasting the two commands suggested into a terminal. It'll prompt for a password, and might prompt for your permission to remove some programs you've tried to installed earlier. If you're unsure what to do, copy the output of your terminal (starting from you typing 'sudo apt-get install -f') and paste the output here.

---

### Post by trginter on 2007-06-19
> **zanglang said:**
> Try copy and pasting the two commands suggested into a terminal. It'll prompt for a password, and might prompt for your permission to remove some programs you've tried to installed earlier. If you're unsure what to do, copy the output of your terminal (starting from you typing 'sudo apt-get install -f') and paste the output here.

That did it.  I ran 'sudo apt-get install -f' and went through the whole thing and everything works great.

Man, I was using XP Pro a few hours ago and Ubuntu is definitely 10x better but I already had to reinstall the OS once because I screwed something up trying to get it to display a wide screen resolution and now I somehow messed up the Add/Remove Applications control.  Is there a "System Restore" type action where I can undo something if I screw it up?

---

### Post by zanglang on 2007-06-19
Unfortunately no, but work is underway to implementing something similar i think. :P

---

### Post by zvacet on 2007-06-19
**system>administration>software sources>chek all boxes>reload**

---

