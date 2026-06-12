---
title: "Ubuntu/ Dual boot Questions"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by DerekBaker on 2007-08-31
An Ubuntu LiveCD saved my butt the other day when I had trouble with Windows. Now I want to install Ubuntu 7.04  as an emergency option without the performance hit of the LiveCD.

This is first experience with both Linux and dual booting.

I have two drives: C for Windows XP Home and P for backup and scratch use. Is it better two put Linux on the same drive as Windows or on the other drive?

Also is it possible to set Windows as the default and only load Ubuntu when I press a certain key on boot?

Thank you

---

### Post by jombeewoof on 2007-08-31
> I have two drives: C for Windows XP Home and P for backup and scratch use. Is it better two put Linux on the same drive as Windows or on the other drive?{/quote]
it doesn't really matter. 
If you can resize your partition through windows with partition magic or a similar program it will be easier, but ubuntu has gparted so even that doesn't matter

as long as you have about 15gigs of space as unpartitioned somewhere you can install ubuntu to it easily.

just make sure during the install you DO NOT use the automatic/guided partitioning. Use the manual version and give yourself a gig for swap and the rest for /    (that is root. that is really the only partition you need to setup)

[quote]Also is it possible to set Windows as the default and only load Ubuntu when I press a certain key on boot?
yes and it is very well documented. 
When you have ubuntu installed go to a terminal and type

```
sudo nano /boot/grub/menu.lst 
```

read that file and do what it tells you to do. if you still can't get it to default into windows. we'll help you out.

---

### Post by DerekBaker on 2007-08-31
15 Gigs? Was only going to give it 10. Will only really be used for internet access.

Why not the automatic/guided partitioning?

Thanks

---

### Post by abhilash82 on 2007-08-31
You need to partition your hdd to accomodate a ext3 and swap partition for Linux. This can be done when you install from the Live CD. If you want it as a temporary option you can also try Wubi. [http://wubi-installer.org/](http://wubi-installer.org/)

A complete guide to dual boot install can be found here [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).

---

### Post by jombeewoof on 2007-08-31
10 should be fine.
The automatic partiitoning in my experience is not all that friendly with the data you want to keep.
your results may vary, but I personally would rather have control of the partitioning process. Ubuntu makes it very easy even if you're relatively new to working with partitions.

---

### Post by mlentink on 2007-08-31
Just to other pieces of advice:
1. be sure to backup all your current programs and data
2. If you decide to install Ubuntu on the same physical drive as Windows, be sure to defragment in windows not once, not twice, but several times. It will help the Ubuntu installer keep your data safe.

---

### Post by DerekBaker on 2007-08-31
Looking at /boot/grub/menu.lst

My Windows entry looks different to one that I saw on a thread here about defaulting:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
 

Do I move the whole of that up?


Thanks

---

### Post by jombeewoof on 2007-08-31
You can either move it toward the top of find this line
```
default         0
```
and then look through the file counting the number of times you see 

```
title           
```
starting at 0 and change the number.

yeah, it's usually easier to just move the 
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
up toward the top.


EDIT
make sure you use your information and not mine. all that map hd0,1 etc... means something to grub

---

### Post by DerekBaker on 2007-08-31
I've moved the entry up; how do I save the changes?

Thanks


[EDIT:] Never mind I've found it.

---

### Post by jombeewoof on 2007-08-31
using vi
hit esc to enter command mode.
the :wq

the : means you are entering a command the w means write and the q means quit

nano I think it's ctrl+x

---

### Post by gn2 on 2007-08-31
[http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

---

