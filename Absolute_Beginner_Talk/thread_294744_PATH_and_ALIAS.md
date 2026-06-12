---
title: "PATH and ALIAS"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by arngrim on 2006-11-07
Hi,

I have two questions. But I guess the answer is the same...

When I try to set a new path with export PATH=$PATH:/Path/To/Add  it works fine in my current session. But if I restart my computer this new addition to the path line is gone. The same problem applies if I make new alias. How do I change this permanently?

In advance: Thanks!

Best,
arngrim

---

### Post by kidders on 2006-11-07
Hi there,

Your PATH is just an environment variable, so it's forgotten the moment you log out. You could set it in one of your startup files though, like ~/.bashrc maybe.

---

### Post by arngrim on 2006-11-07
Using .bashrc worked fine! Thanks!

arngrim

---

