---
title: "where to &quot;see&quot; memory chips?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-09-22
How do I find out what ram memory chips I have?
I can open the laptop and see them physically, I think, but I can't see from there how much memory one or the other has.
I want to find out if a 128 Mb sdram that is offered to me would be of any use. As far as I know, I only have 128, but I see 4 chips there in a row and no empty slots as far as i can understand.

---

### Post by wombat20 on 2006-09-22
Not really an Ubuntu question, but I recommend checking with the manufacturer of your laptop.  Doing a google search for the model number might help.

---

### Post by 1002285 on 2006-09-22
I thought this could be checked somewhere from system information - from Ubuntu.
Thanks anyway.

---

### Post by podunk on 2006-09-22
You can use the "System Monitor". On the top menu bar
System
Administration
System Monitor

---

### Post by steve.horsley on 2006-09-22
The command 
**lshw | less**
will tell you a lot. Type 'q' to quit the listing.
or **lshw > hw.txt**

---

