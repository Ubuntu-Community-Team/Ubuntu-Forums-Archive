---
title: "can't send mails form Evolution"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-12-24
Hi all,

My Evolution (mail client) woes continue! After struggling for a few hours, I finally managed to transfer evolution from one computer to another one (both using Ubuntu 7.10). But now I am not able to send mails from the new computer using SMTP though I can receive mails using POP; on the old computer I can both receive and send mails. I double-checked the account details on the new computer and everything (pop server address, smtp server address, passwords, etc.) seems to be correct.

I am totally at a loss as to what is going wrong. Any suggestions will be of help.

Aam-aadmi

---

### Post by linop on 2007-12-24
Does your email service use a relay that requires a port other than the usual port 25 to be used ?  If so, adding :80 for port 80 (mine uses port 80) at the end of the smtp setting would fix this.

---

### Post by aam-aadmi on 2007-12-24
It was a silly mistake I was making; since I had archived my evolution data from the computer in my office and installed them in my new laptop at home, the smtp server address needed to be changed (because I have a different ISP) at home! Once I changed that everything works fine.

But I must say that transferring the evolution data from one computer to another was not as smooth as I had expected. I had to do a fresh install of Ubuntu to get Evolution to correctly import all my data from the older computer (which I had archived and saved in an external hard drive).

---

