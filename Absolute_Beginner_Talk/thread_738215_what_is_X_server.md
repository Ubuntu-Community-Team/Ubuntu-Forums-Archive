---
title: "what is X server????"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by unclejac on 2008-03-28
Hi, 

I've seen this part before: 

[I]Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again. [/I]

Sometimes happens to me when I log on and off between users, Screen goes white. So I switch to CTL+ALT+F1. Logged in and tried:

```
sudo killall gdm
```

```
sudo /etc/init.d/gdm restart
```

or was it

```
sudo /etc/init.d/gdm start
```

Then try switching back to CTL+ALT+F7 

hmmm not sure thats the solution tho.

---

