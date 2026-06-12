---
title: "Laoding Modules at Boot"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Sweet Mercury on 2007-06-10
In looking up solutions to get my suspend working, I came across a walkthrough which asked me to edit my /etc/modules file. Can I add 'ndiswrapper' to this file so I can stop having to type in *sudo modprobe ndiswrapper* to load my wireless every time I boot my machine? Will cause boot issues if I do?

---

### Post by Stephen Howard on 2007-06-10
worth a try - it shouldn't kill anything if it doesn't work.

---

### Post by Sweet Mercury on 2007-06-10
> **Stephen Howard said:**
> worth a try - it shouldn't kill anything if it doesn't work.

Not only did it not kill anything, It fixed my problem!

Thanks for the response.

---

