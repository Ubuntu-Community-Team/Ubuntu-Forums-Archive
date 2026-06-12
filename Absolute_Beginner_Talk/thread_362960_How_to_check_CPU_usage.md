---
title: "How to check CPU usage?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Viherkaali on 2007-02-16
When I'm using Firefox my computer, it suddenly starts to feel slow, fps is low and everything takes some time to load, is there any way to check my CPU usage in Ubuntu?

If there is, how?

---

### Post by laidback on 2007-02-16
System>Administration>System monitor might help

---

### Post by Viherkaali on 2007-02-16
Well, thanks.

I'm kinda blind ;)

---

### Post by laidback on 2007-02-16
Doubt it, it's just all a bit overwhelming to begin with. I'm the same.

---

### Post by highneko on 2007-02-16
And from a terminal you can use the command top.

---

### Post by jordanmthomas on 2007-02-16
I'd suggest using top over using gnome-system-monitor personally.

On my computer gnome-system-monitor uses like 20% of my CPU just to make its pretty graphs.

top will give you a better idea of what kind of usage you're looking at.

---

### Post by maxamillion on 2007-02-16
> **highneko said:**
> And from a terminal you can use the command top.

```
sudo aptitude install htop
htop
```

its much nicer ;)

---

### Post by jordanmthomas on 2007-02-16
I have seen htop before and not realized it.  I had wondered how people had pimped out top like that....well, not enough to investigate, but I did think it was cool.

```
alias top='htop'
``` is totally going in my bashrc!  Thanks.

---

### Post by highneko on 2007-02-16
> **maxamillion said:**
> ```
sudo aptitude install htop
htop
```

its much nicer ;)

Interesting, thanks.

---

### Post by laidback on 2007-02-16
htop nice one...thanks for that.

laidback

---

### Post by john.nicholls on 2007-02-16
For a graphical, real-time display of cpu usage, install gkrellm.

---

### Post by Quintin Riis on 2007-02-16
Right-click a panel, > add to panel > system monitor.  

I have mine set to show User, System, Nice in bright green, IOWait and Idle are in black.  I also have a Load bar too.  Rather helpful, I think.

---

