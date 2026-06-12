---
title: "how to list booting process at booting time"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-11-17
when system is booting ,it shows something (the list of programs and process are starting)..
is there any idea to save the list in any where (like a text file) or already will it be saved in any file (like log ,etc...)

---

### Post by aa.ivanov on 2007-11-17
At boot linux normaly shows debug info about detected hardware, and starting of the very basic services. You can see all the messages from the last boot with the dmesg command. I think (sory I'm on a public windows box at ATM) this was stored as file too - try /var/log/dmesg

---

