---
title: "How I can terminate Xephyr command that i have execute?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-13
Hi
thank you for reading my post
I have executed: [code ]Xephyr :1 & export DISPLAY=:1; [/code]and then i closed xterm? window.
Now I can not execute this command until i restart my computer, is there some other way to get rid of last execute command an run a new one?

I am learning so i amy use this command 100  times and it is time consuming to restart the computer.

Thanks

---

### Post by Keith Hedger on 2008-01-13
try ```
sudo killall Xephyr
```

---

