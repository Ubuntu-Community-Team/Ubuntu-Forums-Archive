---
title: "Cant boot Fiesty b/c hd is too full"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by rofldangerous on 2007-06-01
Hey, i need help clearing up some space on my hard drive for my laptop, i had an online ubuntu book, but i cant get to it for help. if someone could get back to me asap, it would be much appriciated. my personal email is **[edit]**not a good idea to include your e-mail here unless you like spam**[/edit]**

thanks

---

### Post by raja on 2007-06-01
If you are not able to boot in at all, use the live cd to boot again, delete unwanted files from your hard drive and get some space.

---

### Post by ryanVickers on 2007-06-01
Yes, also, I would expect windows to do something like this, but not ubuntu!  Is your swap not working proporly?  I thought *one* of the reasons of having swap was to fix this?

---

### Post by Ek0nomik on 2007-06-01
> **ryanVickers said:**
> Yes, also, I would expect windows to do something like this, but not ubuntu!  Is your swap not working proporly?  I thought *one* of the reasons of having swap was to fix this?

Swap is for RAM, not Hard Drive.

---

### Post by taurus on 2007-06-01
If you are talking about Ubuntu on your harddrive, then boot into recovery mode form GRUB menu and run

```
aptitude clean
df -h
```

---

