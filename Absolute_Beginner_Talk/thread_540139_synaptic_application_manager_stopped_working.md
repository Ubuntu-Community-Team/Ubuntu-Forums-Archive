---
title: "synaptic application manager stopped working"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by felipebarroeta on 2007-09-01
Hello...

Ubuntu has given me some headaches...  the last one was that synaptic application manager (i have it in Spanish) stopped working, so i cant install anything else. That's not very good.

I get this when I try to use it:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't know what's "dpkg". I have no idea, i'm new with this software. Somebody knows?

I'm also having problems with my windows partition, i guess it's having problems due to the two partitions, but i don't know... if someone could help me with that i'd appreciate it. Windows wont start... hope i can say that here...

See you! Peace!

----

"la gloria yace en ser útil"

---

### Post by ffi on 2007-09-01
run (ie. copy and paste the following in a terminal) *sudo dpkg --configure -a* from a terminal and see if that fixes your problem, else paste the output back here

---

### Post by felipebarroeta on 2007-09-01
hi!

i got this:

Tiene 1 paquete roto en su sistema
*You have 1 broken pack in your system*

Use el filtro «Rotos» para encontrarlo.
Use the filter "broken" to find it.

Where should i use that filter, at the terminal? At synaptic?

Thanks for the help always!!

---

### Post by Perfect Storm on 2007-09-01
Go to synaptic 

Edit tab ---> fix broken package 
Then apply.

---

### Post by ffi on 2007-09-01
You can find it in synaptic under one of those buttons on the bottom right, alternatively follow this guide:

[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)

---

