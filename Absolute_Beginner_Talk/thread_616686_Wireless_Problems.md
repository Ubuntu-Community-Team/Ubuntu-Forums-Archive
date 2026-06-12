---
title: "Wireless Problems"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by RandomCake on 2007-11-18
Hi, I installed Ubuntu 7.4 from Windows and my wireless worked fine (an Intel Pro/Wireless 3945ABG), but now that I have upgraded to 7.10 the network device has just disapeared, excuse my n00bishness but I'm completely new to Ubuntu so any advice on how to sort this out would be great!

Thanks,

RandomCake

---

### Post by Achetar on 2007-11-18
Try this:
```

sudo modprobe ndiswrapper

```

that may do it.
It did it for me when I upgraded to 7.04, also, I am not sure how to add it to autostarts, as it requires root access

---

