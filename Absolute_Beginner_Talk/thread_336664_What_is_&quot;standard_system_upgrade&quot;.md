---
title: "What is &quot;standard system upgrade&quot;?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by maxyfc on 2007-01-11
Hi,

I've just received the Ubuntu Security Notice (fetchmail vulnerability). It suggests that I perform a "standard system upgrade". I'm still new to Ubuntu and Linux and the notice left no clue on how perform to this upgrade.

Is the command "sudo apt-get upgrade" used for a standard system upgrade? I tried it and it didn't upgrade any packages. It also mentions that the linux-image-server package has been kept back. What does this mean?

Thanks in advance.

---

### Post by d3v1ant_0n3 on 2007-01-11
I think it just means to do a full update.

To do it in Synaptic you would 'Reload', 'Mark All Upgrades' and 'Apply' (If Apply becomes active. If not, you're up to date.)

In Terminal, do```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If you get no updated package, then you're up to date.

---

