---
title: "How do i set ubuntu to share my Internet from my XP machine?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by blop on 2007-10-23
Hi i wish to share internet from my XP Pro machine that has 2 LAN cards to my Ubuntu Gutsy laptop. My internet comes to my XP machine via an ethernet cable from a DSL router/modem....so i want the other LAN card to pipe it to my laptop.

Is there an easy way of doing it?

cheers!

---

### Post by Pumalite on 2007-10-23
Would be better to put a D-Lynk router in the middle and provide DHCP to both computers.

---

### Post by blop on 2007-10-23
Hi, thanks for the quick reply..

Well i have a router downstairs but only 1 ethernet cable running upstairs....so i would like to provide internet to my computer and laptop from that one pipe without anyother boxes.

---

### Post by rockmanac on 2007-10-23
WiFI?

-A

---

### Post by blop on 2007-10-23
I really want to use Internet connection Sharing...

and i have ran the XP wizard but it does not work do i need to use a crossover cable? Or will a regular cable work?

---

### Post by Pumalite on 2007-10-23
Why not?

---

### Post by blop on 2007-10-23
why not...what?

I dont understand...

:)

---

### Post by Pumalite on 2007-10-23
Why not wireless.

---

### Post by blop on 2007-10-23
a. means buying new equipment

b. i think i have the hardware to do it already

c. wireless is crud

---

### Post by deputy on 2007-10-23
After running the internet connection sharing wizard on XP, make sure on Ubuntu to have your ip address automatically assigned. Check in System->Administration->Network. In Gutsy, I had to have my Ethernet connection properties to "Enable Roaming Mode". That worked for me and allows me to use the internet connection from my XP pc. Only problem is I can't access Xp shared folders from Ubuntu, but I can access Ubuntu shared folders from my XP.

---

### Post by blop on 2007-10-23
do i use a crossover cable or a regular CAT 5?

---

### Post by deputy on 2007-10-23
You should only use a crossover if you're connecting the two pc's directly, without a router/switch/hub between them, otherwise use a straight through cable.

---

