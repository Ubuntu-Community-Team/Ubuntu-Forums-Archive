---
title: "3D graphics"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Gildp67 on 2007-11-07
I have a NVIDIA Ti 4200 and I want to be able to set the included games to 3D but it tells me I am not able to. Any thoughts as to why I cant? Again I am new to Linux so be gentle

---

### Post by dcstar on 2007-11-07
> **Gildp67 said:**
> I have a NVIDIA Ti 4200 and I want to be able to set the included games to 3D but it tells me I am not able to. Any thoughts as to why I cant? Again I am new to Linux so be gentle

The forums are full of posts detailing how you can install the Nvidia drivers, just do a search and pick one that you feel comfortable with and try it.

---

### Post by Gildp67 on 2007-11-13
Ok I went over to the Nvidia website and found the x86 Linux drivers for my card. would these be what I am looking for to use as drivers for Ubuntu. With all the different drivers that seem to available for Linux based Os's I'm somewhat confused.

---

### Post by rudeboyskunk on 2007-11-13
A better idea is to install envy.  I am not sure if it is in the repositories are not (I'm at work at a Windows computer at the moment).  Go to System>Administration>Software Sources and enable all of the repositories.  Then open up a terminal and type these three commands:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install envy
```

If envy installs, it should help you install the drivers and everything for your nvidia card.

Good luck!

---

### Post by Gildp67 on 2007-11-13
OMG THANK YOU!!!!! works much better

---

