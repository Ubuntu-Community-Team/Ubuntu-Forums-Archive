---
title: "help me please"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2007-11-16
i cant connect to the internet no matter what i do my network card is built into my motherboard.
its is a Realtek RTL8139/810x Family Ethernet NIC

heck when i log into ubuntu my router doesn't even pick up  the machine as being connect

can anyone help me:confused:

---

### Post by shad0w_walker on 2007-11-16
What version of Ubuntu are you using? It seems strange as Ubuntu should work fine with the card (I believe my last system was a realtek and it worked fine)

---

### Post by moondoggy17 on 2007-11-16
i'm using ubuntu 7.10

---

### Post by moondoggy17 on 2007-11-16
what is wrong with it

---

### Post by shad0w_walker on 2007-11-16
Did you notice if the network was working during the install? Assuming you used the LiveCD. 

Also, you could try this:

```

sudo modprobe 8139cp
sudo modprobe 8139too

```

---

### Post by moondoggy17 on 2007-11-16
I did not download the live cd
:lolflag:

---

