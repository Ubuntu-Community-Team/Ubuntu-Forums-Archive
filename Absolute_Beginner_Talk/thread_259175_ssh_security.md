---
title: "ssh security"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-09-17
I recently installed Tor and it works very well. I notice I can use Tor when I ssh into my machine but I have a question on this. Does Tor's proxy server obtain my password if I do that since I am first connecting to their server, then out to my machine? Curious on how this really works and if it posses a security issue or not.

---

### Post by bernied on 2006-09-17
I don't know what tor is but, in general, if you execute a program from an ssh shell it will execute on the remote machine, and will behave exactly as if you were logged in locally at the machine, except that the output will go to the ssh shell, not to the local display. 
Does this help?

---

