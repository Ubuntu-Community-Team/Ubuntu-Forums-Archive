---
title: "[SOLVED] difference  between suspend + hibernate"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by concerto on 2008-02-06
I have a desk top running Ubuntu.  Is there a difference between suspend and hibernate?  Are they supposed to do the exact same thing?  Mine do.

---

### Post by hyper_ch on 2008-02-06
suspend will use more battery on your notebook than hibernate. With hibernate all the info in the memory is being saved to your swap and the notebook will be virtually turned off.

---

### Post by philinux on 2008-02-06
> **concerto said:**
> I have a desk top running Ubuntu.  Is there a difference between suspend and hibernate?  Are they supposed to do the exact same thing?  Mine do.


You did say Desktop not laptop. I think they are are there by default. I've disable them in for my desktop, so the options dont appear.

---

### Post by mjwhitfield on 2008-02-06
How did you disable them?

---

### Post by marufaberlin on 2008-02-06
Suspend and Hibernate put the processor into different sleep modes, to be specific.
But normally it isnn't that imoportant.

---

### Post by philinux on 2008-02-06
> **mjwhitfield said:**
> How did you disable them?

I used ubuntu-tweak. But you can use gconf-editor.

---

### Post by mcduck on 2008-02-06
Suspend stores all currently open data to RAM, and then powers off the hard disk, display, CPU and other stuff while keeping RAM powered. Hibernate writes all open data to swap partition and then completely powers off the computer.

So, suspend is faster and recovering from suspended state takes very little time, but your computer is using some power even when suspended.

HIbernate takes almost as much time as powering off/starting the machine, but it stores the state of your programs and you can continue from where you left. Hibernating machine doesn't use any power.

---

