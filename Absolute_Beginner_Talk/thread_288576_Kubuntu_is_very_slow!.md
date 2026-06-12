---
title: "Kubuntu is very slow!"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by kedarm on 2006-10-30
Hi!

I recently upgraded to Kubuntu 6.06. And I'm really happy with the way it was working.

However, recently, I notice that it has slowed down. Many times the computer refuses to respond, and I got to restart, losing a lt of unsaved work. 
My best guess is that a lot of unwanted programs are running in the background. I tried the command 'ps ax', and it lists down all the programs. But, I have no idea which ones are essential, and which are just a burden for my comp.

Which are the processes I should kill? And how do I stop them from running at start-up?

Thanks!

---

### Post by blind0wl on 2006-10-30
Open up a console and type

```
top
```

This will give you a run down of the processes running and whats being used by the CPU and memory...see if theres anything you dont need and apt-get remove them :)

If your not sure, post the output and I'll make some suggestions

Cheers

Blindy

---

