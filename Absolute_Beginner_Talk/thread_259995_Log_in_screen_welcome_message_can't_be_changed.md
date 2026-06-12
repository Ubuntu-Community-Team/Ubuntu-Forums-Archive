---
title: "Log in screen/ welcome message can't be changed?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Skylive on 2006-09-18
Hi! everyone, I'm new to Ubuntu, and even so, I already have fallen in love with it. However, I am unable to change the default welcome message and the log in screen. After changing the log in screen and the welcome message, no matter what I do, the settings are not saved.. thus I am still using the standard Ubuntu log in screen... How do I change this?:confused:

---

### Post by CatKiller on 2006-09-18
There's a difference between highlighting a theme and checking the radio button. Perhaps that's what you're missing?

---

### Post by orb9220 on 2006-09-18
Yep that was exactellely what I did the first time around.
Make sure the radio button is checked.

---

### Post by Dinerty on 2006-09-18
> **Skylive said:**
> Hi! everyone, I'm new to Ubuntu, and even so, I already have fallen in love with it. However, I am unable to change the default welcome message and the log in screen. After changing the log in screen and the welcome message, no matter what I do, the settings are not saved.. thus I am still using the standard Ubuntu log in screen... How do I change this?:confused:

```
sudo gdmsetup
```

Then just add/change whatever you require and it should save?

---

### Post by HwyXingFrog on 2006-09-24
I can't even use gdmsetup, anyone ever had this issue and manage to resolve it?

> ~$ sudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

---

