---
title: "[SOLVED] cpu frequency dropdown menu?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by larsdk on 2008-04-02
Hi there,

On my last installation I remember doing something to the cpu frequency applet in order to be able to choose instantly between different modes. Searching this forum I found this command

chmod +s /usr/bin/cpufreq-selector

but I'm not sure what it does - can anyone explain it?

Lars

---

### Post by blazercist on 2008-04-02
i think* its that the cpufreq daemon requires super-user permissions while the applet runs with only user priveledges so basically what youre doing is allowing users to change settings on the cpufreq daemon.

---

### Post by The Cog on 2008-04-02
That command changes the file cpufreq-selector so that regardless who launches the program, it runs with the userID of the program owner which is root in this case. Only root is allowed to change teh CPU frequency settings, to that works out just right then.

The flag that you changed (called setuid) is often regarded as a security risk because anyone can run the program with root priv and if they know of a flaw in the program, they could exploit that flaw to do anything they want - the user access controls will have been bypassed. But it has its uses as you see.

---

### Post by larsdk on 2008-04-03
allright - thanks for the explanations guys. I now have my dropdown menu working - and know how I got there :)

---

