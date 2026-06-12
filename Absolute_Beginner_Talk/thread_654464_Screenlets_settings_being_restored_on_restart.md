---
title: "Screenlets settings being restored on restart"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-31
I have some screenlets running. Each time I reboot, their settings are set to default and "Keep above" is enabled. When I open the settings page for a screenlet, I can see the settings I made but they are inactive and the default settings become active. So I have to unckeck each box and check it again to get my settings back. Why si this happening?

---

### Post by spiderbatdad on 2007-12-31
not sure but how about the "automatically remember currently running apps" selection in session options?

---

### Post by LinuxIsInnovation on 2008-01-01
I have enabled the Save session option but this thing still happens.. I found a cure, I hibernated my PC and the problem is solved **until** I add/modify any screenlet. So if I add a screenlet, I have to hibernate, start the comp again and then reboot to make the things work normal.

---

### Post by jayde6 on 2008-01-01
A semi-solution I found was to go to the .config folder in your home directory. Inside should be a screenlets folder with each screenlets config file inside. If you set it to read only it won't reset the settings on boot. I have noticed that if you log out and log back in the settings are reset regardless but will have the correct settings when you reboot.

Hope it helps,
~Jennifer

---

### Post by LinuxIsInnovation on 2008-01-05
> **jayde6 said:**
> A semi-solution I found was to go to the .config folder in your home directory. Inside should be a screenlets folder with each screenlets config file inside. If you set it to read only it won't reset the settings on boot. I have noticed that if you log out and log back in the settings are reset regardless but will have the correct settings when you reboot.

Hope it helps,
~Jennifer

Nope :( :( Same problem persists..

---

### Post by LinuxIsInnovation on 2008-01-11
bump.

---

