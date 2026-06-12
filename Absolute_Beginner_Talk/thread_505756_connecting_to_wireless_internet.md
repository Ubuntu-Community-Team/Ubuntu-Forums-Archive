---
title: "connecting to wireless internet"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by wshadden on 2007-07-20
I am using Ubuntu Linux on my laptop.It is a dual boot laptop. Windows XP and Ubuntu. When I am in Windows, I can access the internet wirelessly. When I am in Ubuntu, I cannot access the internet.
What do I need to do  to get Ubuntu on the internet?

---

### Post by Majorix on 2007-07-20
Did you try ndiswrapper? This tool is supposed to let you run your Windows wireless drivers on your Linux machine. Since your Windows drivers seem to work, you will get going with ndiswrapper.

You can install ndiswrapper by typing this in a terminal:
```
sudo aptitude install ndiswrapper ndisgtk
```

Ndisgtk is just a graphical tool to use ndiswrapper if you prefer it that way. If not, you can remove it from the code above.

Good luck!

---

