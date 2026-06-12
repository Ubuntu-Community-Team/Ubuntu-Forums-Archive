---
title: "No dick space = unable to login"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Mikkel Nielsen on 2007-04-29
When I try to login I get a message that says that "GDM can't write to your approvalfile (at least that's what it translates to from danish)" and it says that this is due to lacking disk space. I was aware of the fact that I didn't have any disk space left when I turned off my computer the last time, but I did'nt think that I would be unable to login and delete some stuff.

I'm missing my ubuntu, windows is so slow, what do I do?

---

### Post by mcduck on 2007-04-29
Boot into recovery mode (from Grub menu) and remove some files that way. You can probably get enough free disk space just by running 'apt-get clean' (it removes cached .deb packages).

(Recovery mode works because it logs you in as root and 5% of disk space is always reserved for root user only, just for situations like this.)

---

### Post by Spike-X on 2007-04-29
No what now??

---

### Post by Lord Illidan on 2007-04-29
I love this thread title :)

Log into recovery mode and delete some files with rm

---

### Post by Mikkel Nielsen on 2007-04-29
It worked! I n00bed my way into recovery mode and used the "apt-get clean" command and then followed upon whatever appeared. I now have a massive 980 Mb of free disk space, very odd.

Thanks for the help :lolflag:

---

### Post by xpod on 2007-04-29
> It worked! I n00bed my way into recovery mode and used the "apt-get clean"

Sounds painful:wink:

---

### Post by Spike-X on 2007-04-29
> **xpod said:**
> Sounds painful:wink:

Not as painful as not having any space for...er...never mind!

---

### Post by xpod on 2007-04-29
> Not as painful as not having any space for...er...never mind!

Thats just stretching things a wee bit too far is it not:)

---

### Post by Spike-X on 2007-04-29
So to speak...

---

