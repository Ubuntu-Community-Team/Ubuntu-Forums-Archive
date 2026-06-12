---
title: "Ubuntu Hard Crashes - starting to really do my nut!"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by mells on 2007-03-11
Please could someone help me. 

My Edgy install keeps crashing on me. Its started doing it after months and months of brilliant stable performance.

I get no warning it just crashes. The only way to unlock it is to hold the power button for 4 secs.  I've noticed it only used to do it not long after startup but now it seems to be crashing randomly.

Please could someone tell me what I need to post to establish what is crashing it.

I dont think its hardware based as my Windows XP partition is 'stable' I'm gutted because I've been singing Ubuntu's praises for months and now I'm having to use Windows again :mad: 

Many Thanks

---

### Post by nudnik on 2007-03-11
> **mells said:**
> Please could someone help me. 

My Edgy install keeps crashing on me. Its started doing it after months and months of brilliant stable performance.

I get no warning it just crashes. The only way to unlock it is to hold the power button for 4 secs.  I've noticed it only used to do it not long after startup but now it seems to be crashing randomly.

Please could someone tell me what I need to post to establish what is crashing it.

I dont think its hardware based as my Windows XP partition is 'stable' I'm gutted because I've been singing Ubuntu's praises for months and now I'm having to use Windows again :mad: 

Many Thanks

You could begin by running a scan of the Edgy partitions by typing "fsck" from a command line. This will check the install for errors and attempt to fix anything that has gone awry. 

If that doesn't produce any tangible results, try running memtest and see what crops up.

---

### Post by mells on 2007-03-11
I typed:

> sudo fsck

and anwered 'Yes' to continue. It the stopped saying bad blocks.

Instantly I was told that I had run out of disk space (there is about 10 gigs free), I couldn't access  the Linux partition.

Tried to reboot and the system crashed and now I can boot my XP partition.

Any ideas on how to fix this? I'm totally screwed. I have work on that partition etc and I need to at least get that off before I start from scratch. :(

---

### Post by astrolabio on 2007-03-11
Did you ruled out hardware issues? have you tried to use Windows for example to see if it crashes too? Have you tried to make a memtest (it should be one of the choiche that grub gives you at the boot)?

EDIT: never mind. I didn't read the comment above.

---

