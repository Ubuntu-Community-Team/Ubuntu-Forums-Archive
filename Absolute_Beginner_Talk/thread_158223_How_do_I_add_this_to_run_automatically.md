---
title: "How do I add this to run automatically?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by starchildmom on 2006-04-10
I got my wireless working and learned a lot in the process, but I still need to run  ```
sudo modprobe ndiswrapper
``` from the terminal every time I boot and the go activate the connection in Network Manager. 

How do I make these tasks happen automatically when I boot up?

---

### Post by karthik085 on 2006-04-10
Add ndiswrapper to /etc/modules

---

### Post by starchildmom on 2006-04-10
[QUOTE=karthik085]Add ndiswrapper to /etc/modules[/QUOTE]

Thank you! It worked.:)

---

