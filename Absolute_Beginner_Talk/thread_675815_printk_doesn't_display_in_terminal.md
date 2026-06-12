---
title: "printk doesn't display in terminal"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by GummB on 2008-01-23
I'm an absolute newbie.
Reading through Oreilly's Device Driver book and trying to get hello world to work.

the "printk" prints properly to /var/log/messages but will not print on the terminal.

cat /proc/sys/kernel/printk yields "4 4 1 7"

I've even tried setterm -msglevel 8

Please help on getting "printk" to actually print to the terminal.. thanks.

---

