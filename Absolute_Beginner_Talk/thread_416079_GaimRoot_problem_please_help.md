---
title: "Gaim/Root problem please help"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by MikeyRibbs on 2007-04-20
When I'm trying to install this plugin it says I don't have permission and only root does. But it wont let me log into root at the start screen, it says no root logins allowed. So are there any alternative ways or can you make it so I can login to root? Some one just help please.

---

### Post by taurus on 2007-04-20
Run the command from a terminal with the sudo in front to install it.  Otherwise, type

```
gksudo nautilus
```
and drag it to where you want to move it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MikeyRibbs on 2007-04-20
Thanks, that worked but now when I go to the plugin menu it doesn't show up on GAIM, any ideas?

---

### Post by orb9220 on 2007-04-20
Where did you install it?
Did you shutdown gaim and restart?

My install shows plugins in   /usr/lib/gaim

---

### Post by MikeyRibbs on 2007-04-20
I installed it there. I restarted gaim but not my computer.

---

### Post by llamakc on 2007-04-20
Why aren't you using sudo?

---

