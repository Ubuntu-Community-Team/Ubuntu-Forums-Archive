---
title: "Can't fix Cinelerra error"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-07-15
Hi, I'm trying to run Cinelerra but I keep getting this error:

```
void MWindow::init_shm():WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

I tried doing "sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax" but it says 
"bash: /proc/sys/kernel/shmmax: Permission denied"

I've already tried the fix kr152ta suggests [here]("http://ubuntuforums.org/showthread.php?t=399941").  It didn't do anything for me.

Could someone help me out here please?

---

### Post by Keen101 on 2007-07-15
Sorry can't help.  But, I hope someone out there does know the answer. I would like to know how to fix this too!


for me I just Ignore it. I have also tried doing the "echo "0x7fffffff" > /proc/sys/kernel/shmmax" as root, but it comes back later.


-keen101

---

### Post by cor2y on 2007-07-16
Taken from a post by efreddi
> Cinelerra started giving the error message regarding *shmmax*. This should be the amount of memory shared between process by the kernel. After some work with google I found an easy solution - in the terminal I gave:
[INDENT]**sudo gedit /etc/sysctl.conf**[/INDENT]and at the end of this file I added the line
[INDENT]***kernel/shmmax=0x7fffffff***[/INDENT]I saved the file and I made
[INDENT]**sudo sysctl -p**[/INDENT]Now cinelerra run fine.
It's a very powerfull software, it's worth some troubble.
Ciao

---

### Post by DrClaw27 on 2007-08-22
Thanks cor2y that worked for me!

---

### Post by Keen101 on 2007-11-11
> **cor2y said:**
> Taken from a post by efreddi
Quote:
Cinelerra started giving the error message regarding shmmax. This should be the amount of memory shared between process by the kernel. After some work with google I found an easy solution - in the terminal I gave:

    sudo gedit /etc/sysctl.conf

and at the end of this file I added the line

    kernel/shmmax=0x7fffffff

I saved the file and I made

    sudo sysctl -p

Now cinelerra run fine.
It's a very powerfull software, it's worth some troubble.
Ciaoi

the above also worked for me! 

zhinker if you have fixed the error on your comp, then you should mark this thread as [solved].

---

