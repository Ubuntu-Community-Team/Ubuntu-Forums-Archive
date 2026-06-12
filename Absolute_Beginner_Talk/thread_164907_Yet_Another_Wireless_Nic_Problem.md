---
title: "Yet Another Wireless Nic Problem"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-23
Here we go...

I am using a compaq v2000 with a broadcom wireless unit,
I have installed the bcmwl5.inf drivers as that is the correct driver as far as I can tell.
](*,) SO, when I go to check the status of it, it says that the card is not found.

If anyone is willing to help that would be awesome, but please keep it very simple as I am trying to break off my windows roots ;) 
Step by step would be greatly apprecitiated.:p

---

### Post by Papa-san on 2006-04-23
Gotta love bcom!

I fought for weeks!
Try the links in my signature. 
Also, be sure the driver is OK. I had a corrupt one for quite a while, and it drove me nuts. There is also a bcmwl5a.inf that gets used for some cards. My links will explain how to find your cards pciid. Then use ndiswrapper list (In links!) to find out for sure...

Good luck!

Edit: Sorry, If you could open a terminal and post the output for ```
iwconfig
```

---

