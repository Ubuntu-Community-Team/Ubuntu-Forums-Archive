---
title: "Startup Question"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by photomaster106 on 2007-01-29
When I restart I notice cman cannot be loaded.
What is cman?
Is this important to load this module?
If it is how do I correct  the problem and load it?

---

### Post by photomaster106 on 2007-01-30
???

---

### Post by rccharles on 2007-01-30
> **photomaster106 said:**
> When I restart I notice cman cannot be loaded.
What is cman?
Is this important to load this module?
If it is how do I correct  the problem and load it?

While I could not find cman on my system, this command should reveal what package cman is part of:

Applications > accessories > terminal

dpkg-query -S "cman"

dpkg-query -L "packagename"

man dpkg-query 

for more info



You may want to look in you log and post the exact message:

dmesg | less

dmesg | grep "cman"



Robert

---

### Post by rccharles on 2007-01-30
> **photomaster106 said:**
> When I restart I notice cman cannot be loaded.
What is cman?
Is this important to load this module?
If it is how do I correct  the problem and load it?

You could also try:

Applications > accessories > terminal



sudo find / -iname "cnam"

Remember to enter your logon password

sudo find / -iname "*cnam*"

---

