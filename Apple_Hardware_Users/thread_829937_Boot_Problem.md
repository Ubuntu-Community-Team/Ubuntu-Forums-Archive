---
title: "Boot Problem"
date: 2008-06-15
forum: Apple Hardware Users
---

### Post by Katz93EMO on 2008-06-15
Hello, I have the following problem.
I had OS X 10.5.2. (leo4allv3) successfully installed on my [Intel-]laptop.
But after restarting my laptop I can not boot leo.
How can I get it in the menu.lst of Linux?

I have added:
title Mac OSX
root (hd0, 6)
chainloader +1
But it comes only: Error Loading booter

Then I tried: 
title           Mac OSX 10.5.2
root            (hd0,6)
savedefault 
makeactive
chainloader     +1
An it comes: Error 12 - Invalid device requested



Thank you.
PS: Sorry for my bad English. ^.^

---

### Post by LaRoza on 2008-06-15
What Mac do you have?

---

### Post by Katz93EMO on 2008-06-15
Sorry, I have no Mac.

---

### Post by LaRoza on 2008-06-15
> **Katz93EMO said:**
> Sorry, I have no Mac.

OS X is supposed to run on Macs only and until it is contested in court, it is illegal to run it on other hardware. Sorry, but this forum doesn't allow discussions on illegal topics (no matter how strange the EULA is)

---

