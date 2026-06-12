---
title: "Grub is gone ?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by DarkAgdistis on 2007-10-08
Hi,

this might be an easy one to answer but as I don't want to do stupid things, I prefer to ask first.

I have installed on my hard drive :

- Win XP ( french ... yes my mum uses the PC :) )
- Ubuntu
- Win XP ( for work ... thus in english ... yippie ! :guitar: )

I tried to get rid of the Win XP ( english ) installation by overwriting it with Slaxware ... the installation went like a breeze and I can access Slax but the multiboot menu is gone.

If I boot Ubuntu CD and select "repair", will it just repair Grub or do I have to look for another solution ? will I have to perform some settings modifications on my XP, Slax installation ?

Thanks in advance

Cheers
DA

---

### Post by overdrank on 2007-10-08
> **DarkAgdistis said:**
> Hi,

this might be an easy one to answer but as I don't want to do stupid things, I prefer to ask first.

I have installed on my hard drive :

- Win XP ( french ... yes my mum uses the PC :) )
- Ubuntu
- Win XP ( for work ... thus in english ... yippie ! :guitar: )

I tried to get rid of the Win XP ( english ) installation by overwriting it with Slaxware ... the installation went like a breeze and I can access Slax but the multiboot menu is gone.

If I boot Ubuntu CD and select "repair", will it just repair Grub or do I have to look for another solution ? will I have to perform some settings modifications on my XP, Slax installation ?

Thanks in advance

Cheers
DA

Hi this thread may help
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by skymera on 2007-10-08
i would just reinstall grub

1.pop in Live CD
2.open terminal
3.find your drive and partition ubuntu is installed one. example drive 1 partitoin 2
3.type: grub
4.root (hd0,1)
5. setup (hd0)

DONE :D

all commands done in terminal!

---

