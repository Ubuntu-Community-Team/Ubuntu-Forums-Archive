---
title: "system slows to a crawl - hard drive thrashes"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by nathanziarek on 2007-03-27
I have a machine that I VNC into (using remote desktop through the preferences GUI). After about an hour of working on it, it grinds to a halt and becomes completely unresponsive.

As I have ssh installed on the box, I logged in to check out top and see if there was something taking up all of the CPU -- it took 10 minutes to log in. Now that I am in and running top, I see this:

```
top - 10:41:41 up  1:57,  4 users,  load average: 12.59, 13.06, 11.32
Tasks:  96 total,   1 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  6.1%sy,  0.0%ni,  0.0%id, 92.9%wa,  0.6%hi,  0.0%si,  0.0%st
Mem:    254252k total,   250132k used,     4120k free,       76k buffers
Swap:   738948k total,   738948k used,        0k free,     3460k cached
```

The 0k swap line is interesting, although I don't know enough about it to know what that means. Is this just my 256MB catching up with me?

Nothing seems to be taking up any CPU (although I don't know how to sort by CPU usage, nothing at the top of the list is taking up more than 2-3%)

Thanks for any help you can provide,

Nate

---

### Post by m83 on 2007-03-27
One of the applications that you use is leaking memory. See with top what application uses the most memory (press Shift+M to sort by used memory in top).

---

### Post by kpatz on 2007-03-27
Something's eating up all your memory.

While in top, hit O and then O again (that's a capital Oh, not a zero), then hit enter to sort by virtual memory usage (the VIRT column).  The processes using the most memory will show up at the top.

You probably have a runaway process or something that has a memory leak, chewing up all your space.

---

### Post by nathanziarek on 2007-03-27
vino-server is taking up 50% of my memory. Seems like that is the screen sharing (remote desktop / vnc / etc) app that I was using.

Is 50% a lot (seems high looking at the others in the 0.1 - 2.0 range)?

---

### Post by nathanziarek on 2007-03-27
I think that was it. I killed it using kill 3454 (or whatever the pid was) and now the system is running fine again and my free swap space is a nice large number again.

I turned on Remote Desktop by clicking System > Preferences > Remote Desktop   ...   and then choosing the options I wanted and clicking **Close**.

If this is just a buggy app, is there something I can upload that'll help shore it up? Not really "giving back" in the typically sense of the word, I know :)

Thanks for the quick responses!

Nate

---

