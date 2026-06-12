---
title: "[SOLVED] Something cool i alwayed wanted"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by wildgene789 on 2008-01-16
i was just wondering i always wanted to make my computer look difficult when someone starts it up and is there a way to make it start up with like just text that asks me to enter username and password and then it goes into the GUI thing. I dont know i just thought that would be cool lol and maybe make computer start faster.

---

### Post by ckennow on 2008-01-16
Are you using ubuntu or any form of linux without the xserver starting up automatically.  cuz i believe that would accomplish the effect you've described.

If you install the desktop version of ubuntu and then configure your startup configuration(someone help here cuz i don't know which files you would have to configure) then when you boot it will ask you to logon and when you login you'll just type ```
startx
```

---

### Post by wildgene789 on 2008-01-16
yea can someone please supply like a tutorial lol and thanks

---

### Post by Thunar on 2008-01-16
I don't have my Linux machine handy at the moment, but I think what you're trying to accomplish is easy enough... I think in the "System/Settings" or "System/Administration" menu (if you're using Gnome) there's a "GUI" settings, or maybe it's in "Appearance" but maybe in there there's a way to disable a logon GUI. Sorry I couldn't be of more help than that at the moment... 

Good Luck!

---

### Post by thelatinist on 2008-01-16
Just go to System > Administration > Login Window > Local

Choose "Plain" from the "Style" dropdown.  Change background colors, etc., to suit your tastes.

---

### Post by nikoPSK on 2008-01-17
> **wildgene789 said:**
> yea can someone please supply like a tutorial lol and thanks

I know you press control shift f1 or something... :)

---

### Post by sumguy231 on 2008-01-17
If you want to disable graphical login, you need to disable GDM from running on startup. I believe you can do that from System -> Administration -> Services.

---

### Post by nikoPSK on 2008-01-17
> **sumguy231 said:**
> If you want to disable graphical login, you need to disable GDM from running on startup. I believe you can do that from System -> Administration -> Services.

ah, now I got it.

---

### Post by sumguy231 on 2008-01-17
I should also mention that without GDM running you will have to shut down the system from the command line using the shutdown command.

---

### Post by nikoPSK on 2008-01-17
> **sumguy231 said:**
> I should also mention that without GDM running you will have to shut down the system from the command line using the shutdown command.

for clarification:

```
sudo shutdown -h now
```

---

### Post by thelatinist on 2008-01-17
> **sumguy231 said:**
> If you want to disable graphical login, you need to disable GDM from running on startup. I believe you can do that from System -> Administration -> Services.

You can, however, *keep* the GDM in startup and enable the "Plain" Style.  You can customize that to look as colorless and plain-text as you want and still keep the ability to shutdown graphically.

---

### Post by wildgene789 on 2008-01-17
thanks alot guys

---

### Post by nikoPSK on 2008-01-18
no problem, please mark your thread as "SOLVED". :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

