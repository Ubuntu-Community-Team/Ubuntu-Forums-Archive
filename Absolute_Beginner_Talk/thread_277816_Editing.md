---
title: "Editing"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Avarus on 2006-10-15
Stupid question needing a simple answer:

How to edit files like apache2.conf on the server version?

I don't know why but I can't find an answer. Please give me the command so I can continue my explorations :P

---

### Post by PriceChild on 2006-10-15
I don't currently have it installed, but you could do a:
```
locate apache2.conf
```
And then a:
```
sudo nano /path/to/apache2.conf
```
Replacing /path/to with the real path.

---

### Post by Avarus on 2006-10-15
Ok, thank you.

Answer the next question right and win fabulous prizes!

Ok, here is the question: where to find my WAN?

---

### Post by Marsolin on 2006-10-15
ifconfig is the program to use to detect the network connections and IP addresses available to the server. Check out the man page for details on usage.

---

