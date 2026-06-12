---
title: "Problems with serial port"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by luisfranco on 2006-12-21
Hi , i have troubles with serial port, i use Ubuntu 6.0.6 and gtkterm, i work with routers and switches (cisco), when i want connect this device to my laptop (ibm t22) in a port serial , gtkterm cant show me the ios, what can ido ? please help me?

---

### Post by steve.horsley on 2006-12-21
Make sure gtkterm is configured for:
Port: /dev/ttyS0
Speed: 9600
Parity: none
Bits: 8
Stopbits: 1
Flow Control: none

This setup works for me (on a Dell D600). Use the standard Cisco console cable.

---

### Post by luisfranco on 2006-12-21
Hi Steve, i tried with that configuration , and doesnt work, thanks anyway.

---

