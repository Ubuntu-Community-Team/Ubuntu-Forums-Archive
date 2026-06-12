---
title: "Which Build for Pentium D 805?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by msekolpsu on 2006-05-30
I just loaded up the 64-bit PC (AMD64) install CD for my Pentium D 805 since it says that's the 64-bit build, but it only reports one processor instead of two.  Since this is dual core, I thought I should be seeing 2 processors.

When I go to load the linux-686-smp, which is what I've seen recommended, it doesn't run because the build is amd64.

So, should I use the PC (Intel x86) install CD?  Thanks!

---

### Post by halfvolle melk on 2006-05-30
According to [this thread](http://www.ubuntuforums.org/showthread.php?t=85917) you could use one of the following:

```
sudo apt-get install linux-k6-smp
# or
sudo apt-get install linux-k7-smp
```

Both should get the dual core working.

Edit: though it's for AMD ... well. it's worth a shot :)

---

### Post by nudnik on 2006-05-31
I would recomend using the x86 build and then upgrading to the 686 kernel using Synaptic. I have an 820D and this seems to work best for me. 

See my kernel version below:

2.6.15-23-686 smp

---

