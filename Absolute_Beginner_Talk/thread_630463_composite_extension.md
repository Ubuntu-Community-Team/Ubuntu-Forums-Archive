---
title: "composite extension"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by bbrff on 2007-12-03
when i first  decided to get back into linux i downloaded and installed ubuntu 7.1........I liked it a lot and my teens thought the visual effects with the jello-like windows was pretty cool. After some time it came to my notice studio ubuntu which i found intereseting being a guitar player, so i downloaded and installed it but now when I try to get the extra visual effects i get a window popping up saying I dont have composite extensions available. Is there a way around this. thanks in advance

---

### Post by the.dark.lord on 2007-12-03
Do you have restricted drivers enabled? If not, enable them.

If that doesn't work, try this command:

```
sudo apt-get install xserver-xgl
```

---

### Post by bbrff on 2007-12-03
yes i have a restricted ati accelerated graphics driver installed and enabled. I entered the command in the terminal and it still has the same result. do i need to restart the system?

---

### Post by the.dark.lord on 2007-12-03
> **bbrff said:**
> yes i have a restricted ati accelerated graphics driver installed and enabled. I entered the command in the terminal and it still has the same result. do i need to restart the system?

Did it install some files? If it did, restart the computer and try.

---

### Post by bbrff on 2007-12-03
I restarted system and now i have this message "failed to execute child process compiz (no such file or directory"

---

### Post by the.dark.lord on 2007-12-04
> **bbrff said:**
> I restarted system and now i have this message "failed to execute child process compiz (no such file or directory"

Then, I think you don't have compiz installed. Put this command in the terminal

```
 sudo apt-get install compiz

```

and restart, and see if it works.

---

