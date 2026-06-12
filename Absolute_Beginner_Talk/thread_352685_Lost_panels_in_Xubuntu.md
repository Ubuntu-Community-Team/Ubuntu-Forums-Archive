---
title: "Lost panels in Xubuntu"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-02-03
Hi, 

I was exploring the desktop configuration in Xubuntu, when suddenly the panels disappeared. I have tried using the terminal command {xfce4-panel &} which brings back the panel, but it disappears again once I shut down the terminal. 

Shutting down and logging in again doesn't help. After opening the terminal once or twice, I lose the ability to call up the menues from clicking on the desktop. 

On the bright side, when the panels do come up, they retain the configuration I want for them.

---

### Post by shareMenaPeace on 2007-02-03
You could to run this from terminal

```
killall xfce4-panel
```

---

### Post by kerry_s on 2007-02-03
press alt and F2 and type> xfce4-panel

---

### Post by jplowman on 2007-06-01
I just had the same problem and this fixed it. Can anyone explain why?&#12288;What does the xfce4-panel command do?  And any idea why the panel disappeared in the first place?

Thanks for keeping up this very useful resource!

p.s. This is my first post, so to introduce myself, I am a Linux newbie. I just installed Xubuntu a few days ago. I'm running it on a Toshiba Libretto L5 a few years old - I installed it in the hope of gaining some speed over Windows XP, so I'm very interested in tricks to make it run faster.

---

### Post by ugm6hr on 2007-06-02
> **Brendantb said:**
> Hi, 

I was exploring the desktop configuration in Xubuntu, when suddenly the panels disappeared. I have tried using the terminal command {xfce4-panel &} which brings back the panel, but it disappears again once I shut down the terminal. 

Shutting down and logging in again doesn't help. After opening the terminal once or twice, I lose the ability to call up the menues from clicking on the desktop. 

On the bright side, when the panels do come up, they retain the configuration I want for them.

I think the "&" puts the taskbars in the background.  So when you close the Terminal, they disappear, but are still running.  Try it without "&".  And then try saving session for future login when you logout.

---

