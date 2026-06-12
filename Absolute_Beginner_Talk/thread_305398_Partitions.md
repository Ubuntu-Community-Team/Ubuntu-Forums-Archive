---
title: "Partitions"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Darzinho on 2006-11-23
Hi,

I installed Ubuntu last night and I'm very impressed... 

However, I now seem to have a multiplying partition problem (I let Ubuntu partition automatically)

According to my Windows, I now have;

(My Windows partition)19.5gb
(My Ubuntu partition)6.5gb
(No idea)2.2gb
(No idea, but I think it was there before Ubuntu).3gb

Also, that only adds up 20 about 28.5gb. Where's the other 1.5 I paid for and that Ubuntu said was there when I was installing Ubuntu? (That problem was there before I installed Ubuntu.)

Any ideas?:confused:

---

### Post by taurus on 2006-11-23
Open a terminal, Applications -> Accesories -> Terminal, and paste the output of this command here.

```
sudo fdisk -l
```

---

### Post by b_martinez on 2006-11-23
> **Darzinho said:**
> Hi,

I installed Ubuntu last night and I'm very impressed... 

However, I now seem to have a multiplying partition problem (I let Ubuntu partition automatically)

According to my Windows, I now have;

(My Windows partition)19.5gb
(My Ubuntu partition)6.5gb
(No idea)2.2gb
(No idea, but I think it was there before Ubuntu).3gb

Also, that only adds up 20 about 28.5gb. Where's the other 1.5 I paid for and that Ubuntu said was there when I was installing Ubuntu? (That problem was there before I installed Ubuntu.)

Any ideas?:confused:

Just some ideas.
1) The "missing" space may be a 'restore' secton put on your hdd by the manufacturer.
2) The manufacturer may have labeled a gigabyte as 1 billion bits,(base 10) rather than 1073741824 bits .

hth
Bill

edit: 19.5 + 6.5 + 2.2 +0.3 = 28.5

---

### Post by CatKiller on 2006-11-23
> **Darzinho said:**
> Where's the other 1.5 I paid for...?

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

30 x 10^6/2^20 = 28.6

HTH.

---

