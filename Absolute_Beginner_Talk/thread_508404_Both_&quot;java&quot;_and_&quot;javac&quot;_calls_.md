---
title: "Both &quot;java&quot; and &quot;javac&quot; calls javac"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by TM-Nite on 2007-07-24
How can i change the command "java" to make it calls java?
atm both javac (compiler) and java calls the compiler and i cant run any java app :(

thx for the help

Nite

---

### Post by zanglang on 2007-07-24
Did you accidentally changed the symlink for java? Try this:
> sudo ln -sf /etc/alternatives/java /usr/bin/java

---

### Post by TM-Nite on 2007-07-24
> **zanglang said:**
> Did you accidentally changed the symlink for java? Try this:

it works now! thank you so much

---

