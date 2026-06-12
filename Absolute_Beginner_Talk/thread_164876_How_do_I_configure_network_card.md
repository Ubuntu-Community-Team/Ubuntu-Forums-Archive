---
title: "How do I configure network card"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by hfashina@hotmail.com on 2006-04-23
When I went through the Ubuntu install process it said that I do not have a network card installed.  I do and it works in Windows.  Where do I go to manually try to configure my network card?

---

### Post by steve.horsley on 2006-04-23
What type is it?

Can you post the output from the command:
**iwconfig**

---

### Post by hfashina@hotmail.com on 2006-04-23
I fixed by going to terminal and entering

**modprobe ne io=0X300 irq=9**

---

