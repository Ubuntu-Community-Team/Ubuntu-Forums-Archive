---
title: "upgrade to dapper"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-06-16
Yesterday a window asked me if I wanted to upgrade to 6.06 LTS: I answered no.
Tody I changed my mind and I tried to upgrade by Sudo get-apt dist-upgrade
but it didn't work.
What can I do? I looked for any hint in the threads, but no-one seems to help me.

Thanks:D

---

### Post by frodon on 2006-06-16
All about the dapper upgrade is in this wiki page : [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by muep on 2006-06-16
```
gksudo update-manager -c
```

Tell me if it works :)

---

### Post by bruce89 on 2006-06-16
Actually, update-manager should have a button asking if you want to upgrade, if there isn't, press "check"

---

### Post by helphope on 2006-06-16
:p Thanks all for answering.
First I tried gksudo update-manager -c, but it didn't work;
so I saw  [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades), and I tried 
gksudo update-manager.
At the moment the download is still on; it should be finished in half an hour.
I'll let you know.
Bye:-({|=

By the way, the terminal is open: I think that if close it, it would stop the download. Am I right?

---

### Post by user1397 on 2006-06-16
did you open the terminal? or did the update-manager do it?

---

### Post by helphope on 2006-06-16
[QUOTE=erik1397]did you open the terminal? or did the update-manager do it?[/QUOTE]


It was me who opened the terminal.

---

### Post by xenblend on 2006-06-16
Always remember to 'apt-get update' before downloading anything. If you don't like what you're getting you can alter /etc/apt/sources.list but make sure you know what you're adding/subtracting.

---

### Post by helphope on 2006-06-16
[QUOTE=xenblend]Always remember to 'apt-get update' before downloading anything. If you don't like what you're getting you can alter /etc/apt/sources.list but make sure you know what you're adding/subtracting.[/QUOTE]

Yes, I did.
But what is the update manager?

---

### Post by user1397 on 2006-06-17
[quote=helphope]Yes, I did.
But what is the update manager?[/quote]it is the program used to download and install updates for your computer.  it can be found in system > administration > update manager

---

### Post by helphope on 2006-06-22
[QUOTE=erik1397]it is the program used to download and install updates for your computer.  it can be found in system > administration > update manager[/QUOTE]
Sorry man, for answering you only now. I almost forgot.
Thanks a lot:)

---

