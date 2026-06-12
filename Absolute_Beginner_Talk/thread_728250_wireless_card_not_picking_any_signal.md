---
title: "wireless card not picking any signal"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by kemb913 on 2008-03-18
i am very new to ubuntu, and was wondering how to connect to my home network so i can use the internet.

my i have a wireless card in my desktop computer. When i click on the network logo in ubuntu, teh only options it has are:

>Wired Connection (whited out)
>Manual configuration...

Can someone please help me with this? I am very eager about using ubuntu, so any help is greatly appreciated.

Thanks
Kenneth

---

### Post by dstew on 2008-03-18
Probably you need to install a driver to make your wireless card work. To see what your wireless card is, open a terminal window (Applications --> Accessories --> Terminal) and enter this on the command line:```
lspci
```That will give an output of all the devices on your PCI bus that Ubuntu can detect. Post the result on the forum.

---

