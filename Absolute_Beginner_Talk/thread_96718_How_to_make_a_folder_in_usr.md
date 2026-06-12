---
title: "How to make a folder in /usr"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by corlex on 2005-11-29
Hello again :P
No i want to make a folder in /usr but what command do I has to use?
I want it this way: /usr/java
I want to set up the folder <java>

---

### Post by Leif on 2005-11-29
use sudo, but read this first : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

---

### Post by ajgreeny on 2005-11-29
You can only do this as root so open a terminal and then type:-
sudo mkdir /usr/java
That should do it for you.

---

### Post by corlex on 2005-11-29
okay ;) thanks! but now i has to move a file from /home/desktop to /usr/java
anyone that have a command for that? since I just can't move it over.

---

### Post by Leif on 2005-11-29
again, put sudo before it, ie sudo mv x y. be careful about using sudo though, don't use it unless you really really need to. for example, if you're trying to install java, there are easier ways than what you're doing

---

