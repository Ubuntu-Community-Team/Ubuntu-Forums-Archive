---
title: "Disabling monitor power saving mode on Ubuntu Server"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by MoxJet on 2007-04-22
Greetings,

I am using Ubuntu Server 7.04 on one of my computers. I control it via ssh from other computers so it only has a network cable and a monitor plugged in. On the monitor I'm running htop, but screen goes blank after some minutes and I have to press a key to start it up again.

How do I disable this power saving mode? I want my screen to view htop forever!

Thanks in advance,
Dan

---

### Post by MoxJet on 2007-04-22
I think I might have solved this by doing

```
$setterm -blank 0
$setterm -powersave off
$setterm -powerdown 0
```

Posting just in case someone else encounters this.

---

### Post by TechSys on 2007-04-24
I just tried that, since my kubuntu does the same thing. However, the first and last one didn't give any error. The second one came up with "Cannot (un)set powersave mode. I even tried it with on instead of off, came up the same thing.

Oh well. Ain't a big thing though. I like *buntu, but I need more

---

### Post by drklepto on 2008-05-13
> **TechSys said:**
> I just tried that, since my kubuntu does the same thing. However, the first and last one didn't give any error. The second one came up with "Cannot (un)set powersave mode. I even tried it with on instead of off, came up the same thing.

Oh well. Ain't a big thing though. I like *buntu, but I need more

Same issue. I solved figuring out that it wasn't working because I was logged through an ssh session.

Type the commands directly on the console.

Cheers

---

