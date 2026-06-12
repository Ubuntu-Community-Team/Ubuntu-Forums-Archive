---
title: "Limiting internet access"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by CorwinShiu on 2008-03-16
I'm a student that easily gets distracted by the internet whenever I use my computer. This becomes problematic when I use the computer for word processing. So my question is, is there a way to set times when I cannot use the internet through my account? I cannot simply unplug the router since my brother needs the internet to distract himself ;P.

Thanks.

---

### Post by Oldsoldier2003 on 2008-03-16
> **CorwinShiu said:**
> I'm a student that easily gets distracted by the internet whenever I use my computer. This becomes problematic when I use the computer for word processing. So my question is, is there a way to set times when I cannot use the internet through my account? I cannot simply unplug the router since my brother needs the internet to distract himself ;P.

Thanks.

```
sudo /etc/init.d/networking stop
```
or you could set up a cronjob for root to run 
```
/etc/init.d/networking stop
```
when you want the net off.

then run:

```
 /etc/init.d/networking start
```
when you want it back on

---

