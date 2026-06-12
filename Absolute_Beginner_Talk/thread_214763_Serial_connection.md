---
title: "Serial connection"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by cojniz on 2006-07-13
Recently installed Ubuntu 6.06 on my laptop, to try it out. I don't use the laptop for much, other than connecting to serial devices/terminals.
So far I've figured out that your first serialport is called something in the lines of tty.
dmesg | grep tty shows:
serial8250: ttySO at I/O....
Does this mean that ttyS0 is my COM1? How do I use telnet to connect to this port?

---

