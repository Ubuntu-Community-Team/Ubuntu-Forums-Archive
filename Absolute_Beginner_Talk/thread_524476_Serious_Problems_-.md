---
title: "Serious Problems -"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-08-13
Recently my computer has stopped detecting my wireless card (eth0) I didn't make any changes to the system that could of caused this.

I left it unplugged all night and when I plugged it back in my internet was working for about ten minutes then my processor usuage shot up to 100% and I have to restart - when I restart my internet no longer works until I leave it unplugged overnight.

This process can be repeated.

---

### Post by nvrpunk on 2007-08-13
Hardware issue if you have changed nothing software wise.

---

### Post by auraithx on 2007-08-13
What is the command that tells me if my computer is seeing my wireless card?

---

### Post by dwblas on 2007-08-13
lspci lists all of your pci devices.  ifconfig will tell you what network connections you have.  lo is just the local connection, so you should have something like eth0 for wireless.

---

### Post by jmnormand on 2007-08-13
sounds like it could be a heat or power issue killing your wireless card to me, though likely mostly due to a problem with the card if nothing else is effected.  the cpu usage could just be the comp trying to find the card after it goes dead.

---

