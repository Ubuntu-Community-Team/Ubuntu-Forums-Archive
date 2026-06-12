---
title: "Getting wireless to work on centrino laptop"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by sinar on 2006-10-10
Hello,

I'm very new to linux and ubuntu, I was recently given an old broken windows laptop, which I have got to work and have installed ubuntu as I would like to  learn how to use it.

The install went  very well, however I can't seem to get the wireless internet connection working, with both my Apple and Windows computers it just works without needing to be set up.

The laptop is an Acer travelmate 290, and has an Intel Centrino Pentium M 1.3 processor, 40GB hard drive and 256 RAM.

I'd appreciate it if someone could tell me how to set it up so the wireless works, in simple terms if possible. 

I'll be getting a book on ubuntu soon so hopefully I'll be a bit less clueless when I've read that,

thanks for reading,

Julie

---

### Post by jorn on 2006-10-10
What chipset does the wireless use? Have you done a search in this forum?

---

### Post by Splittor on 2006-10-10
You need to find out what chipset it is, see if it's supported, and what methods are required to get it working.

There are many chipsets that already have modules built and don't need to be messed with.

---

### Post by LookTJ on 2006-10-10
post output of

```
ifconfig
```

and

```
iwconfig
```

also try

```
sudo ifdown eth1 && sudo ifup eth1
```

Taylor

---

### Post by Straevaras on 2006-10-10
> **Splittor said:**
> You need to find out what chipset it is, see if it's supported, and what methods are required to get it working.

There are many chipsets that already have modules built and don't need to be messed with.

Windows XP will usually do a good job at identifying your Wireless Adapter, if all else fails trying to find the Wireless chipset used.

---

### Post by Foudre on 2006-10-10
i have a newer laptop that has a centrino, it worked fine, but i had to tell it to enable the device, under netwroking i clicked enalbe, and i can't remember off the top of my head some where in there  you had to tell it the network you want to connect to, this may be too simple for what you need, but it may be what you're looking for, also try installing the wireless assistant program fromt he add/remove programs thingy, its really usefull for connecting to networks

---

