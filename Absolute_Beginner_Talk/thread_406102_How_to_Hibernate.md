---
title: "How to Hibernate?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by mfmbcpman on 2007-04-10
Does the swap space need to be a certain size in order to hibernate? I have been unable to hibernate but my swap is only 256 MB since I have 2GB of RAM.

---

### Post by annda on 2007-04-10
ubuntu has a problem with hibernation. it often doesn't work. i don't think swap is the problem, but i might be wrong.

---

### Post by mfmbcpman on 2007-04-10
Searching around on the topic, there are a lot of instances of people who can't get it to work. With me, I will click on Hibernate then it will bring me to a password prompt to login like it was in standby for a second.

---

### Post by Miguel on 2007-04-11
mfmbcpman,

Although I'm an ATi sufferer, I think your issues might be related to an xorg.conf option. Please browse the forums or google for the following line (an nvidia option):
```

Option NvAGP 1

```

There should be some info in  the Laptop Testing Team\ Dell Inspiron 8600 page, too.

---

