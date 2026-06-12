---
title: "Too many OSes?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-03-31
I installed Ubuntu 6.10 Edgy last week (my first Linux experience) and love it, and am now curious to check out other distributions. So I've burned the openSUSE 10.2 DVD, but am curious that if I install it on top of Vista and Ubuntu, Grub won't recognize at least one of these, and I'll be stuck without connectivity (since my USB wireless adapter was hell to set up), or possibly even worse. 

So here's the hard drive situation

40G -- Windows Vista and Edgy

80G -- where openSUSE will be. 

Any imaginable trouble?

---

### Post by jinx099 on 2007-03-31
Grub should have no problem recognizing all those OS's.  The only problem is if you use opensuse's bootloader to boot edgy, if you get an updated edgy kernel you will have to manually add it to suse's bootloader.  However, you can have suse's bootloader point to edgy's bootloader and you will eliminate that problem.

---

### Post by letitsnow on 2007-03-31
i've got almost the same setup as you, just XP instead if vista. i'm letting openSuse's grub take care of things for now. 

setup was easy, i just let it run and it took care of itself.

---

