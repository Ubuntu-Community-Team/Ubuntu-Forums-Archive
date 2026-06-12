---
title: "Question about a dual boot"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Christopher on 2006-08-18
I recently built a linux machine and i want to get rid of the dual boot on my main pc. Can i go into windows xp's administrative tools/Disk management and delete my linux partition without messing up my windows boot? Thanks in advance.

---

### Post by hopstah on 2006-08-18
it depends on what bootloader you are using.  if you are using grub, then you're going to have some problems.  grub resides on your main linux partition, so wiping that out will also wipe out your ability to boot to windows by way of grub.  you would then have to repair your mbr, but i don't know how to do that without completely installing winxp.

if you are using the windows bootloader, then you will be fine deleting your linux partition, but just make sure to remove the lines referring to your linux partition from your boot info.

---

### Post by Christopher on 2006-08-18
> **hopstah said:**
> it depends on what bootloader you are using.  if you are using grub, then you're going to have some problems.  grub resides on your main linux partition, so wiping that out will also wipe out your ability to boot to windows by way of grub.  you would then have to repair your mbr, but i don't know how to do that without completely installing winxp.

if you are using the windows bootloader, then you will be fine deleting your linux partition, but just make sure to remove the lines referring to your linux partition from your boot info.

I think im using grub.

---

### Post by confused57 on 2006-08-18
Maybe this link can help:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Christopher on 2006-08-18
> **confused57 said:**
> Maybe this link can help:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Thanks for that link.

---

### Post by Christopher on 2006-08-18
> **confused57 said:**
> Maybe this link can help:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Very nice thank you, i booted into recovery console via my xp cd and did a fixmbr and all is good. Then i went into  disk manegment and reformated that part of my drive back to NTFS. Thanks again.

Im 2 games away from running Ubuntu 24/7  ;) .

---

### Post by hopstah on 2006-08-19
what games might those be?

---

### Post by secretlondon on 2006-08-19
> **hopstah said:**
> what games might those be?

Probably all of them...

The number of games that work successfully under linux is pretty small :(

The chances of me ever getting to play Everquest 2 under wine/cadega even smaller..

---

### Post by Christopher on 2006-08-19
> **hopstah said:**
> what games might those be?

Madden 2007 & Everquest 2

---

### Post by Christopher on 2006-08-19
> **secretlondon said:**
> Probably all of them...

The number of games that work successfully under linux is pretty small :(

The chances of me ever getting to play Everquest 2 under wine/cadega even smaller..

Have you tried running EQ2 with Cadega? I play EQ 2 also and was wondering if its worth trying to get it to run under wine or cadega?

---

