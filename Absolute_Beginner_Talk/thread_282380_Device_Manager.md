---
title: "Device Manager"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-22
How do I see all the hardware on my Ubuntu? I want to see the version of my wifi card.

---

### Post by madmetal on 2006-10-22
system >> system management >> device manager
(or something like that, i dont have english menu)

---

### Post by amitroy5 on 2006-10-22
How can I tell what device my wifi uses? What is the hardware that it uses? The model number? Thanks!

---

### Post by dvarsam on 2006-12-02
> **amitroy5 said:**
> How can I tell what device my wifi uses? What is the hardware that it uses? The model number? Thanks!

Well, on my Ubuntu v6.10:

1. From Menu, I select: "System\Administration\Device Manager".

2. I go under: "82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2".

3. Then under: "UHCI Host Controller".

4. Then Under: "D-Link DBT-122".

Well that is my model!

Similarly, you should be able to find yours.

Good Luck!

---

### Post by lamego on 2006-12-02
The following terminal commands are also usefull:
```
lsusb 
lspci
lshw

```

---

