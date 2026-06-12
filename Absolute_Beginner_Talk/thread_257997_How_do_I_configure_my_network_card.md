---
title: "How do I configure my network card"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by mpell on 2006-09-15
My internet on Ubuntu doesn't work i am useing windows to write this, i am dual booted.  I went to the network options and there was no ethernet card there only a dial up modem conection. How di i configure my card so i can get online.

---

### Post by Kobalt on 2006-09-15
Hi,

What model of ethernet card do you have ? It is possible that your card is not recognised by Ubuntu without a bit of configuration or tweaking. Try searching the forum with the model of your card to know if some users already encountered the same problem with the same hardware. 
Can you see you ethernet card when you type this command in a Terminal : 
```
lspci
```
If you could also give us the results of this command (I mean, is there only a "lo" interface listed or do you get a "eth0,1..." interface as well : 
```
ifconfig
```

Cheerio !

---

