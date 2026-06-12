---
title: "Help Help Help Please Wireless Network"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by duncanelliot on 2007-02-05
Hi,

I finally switched to Linux after 10 years of Windows because I was soo pissed off with having to reinstall XP. 

Anyway, after successfully installing Ubuntu, I found that my Belkin F5D7000 wireless card does not work.

Two HOURS later, it still doesn't work. I tried this tutorial:

[https://help.ubuntu.com/community/WifiDocs/Device/F5D7000?highlight=%28f5d7000%29](https://help.ubuntu.com/community/WifiDocs/Device/F5D7000?highlight=%28f5d7000%29)

but I got stuck at step 1.2, ndiswrapper does not work on my computer!!!!! I get an 'command not found'.

SOmeone pleaseeeeee help.

Thanks.

---

### Post by Ptero-4 on 2007-02-05
You need to install ndiswrapper first, hook your computer to the internet (wired offcourse) and type:
```
sudo aptitude install ndiswrapper ndisgtk
```

after you have enabled the universe and multiverse repositories.

---

