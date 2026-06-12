---
title: "couple of newb questions"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by importpsycho on 2007-05-13
Just installed  Ubuntu 7.04 
first time using linux ever!

i have two hard drives, 1 with xp and 1 empty hd
before I installed it the empty hd was 2 partitioned, unformated
when i installed ubt, i picked second hard drive, and after installation it seems to  show only 1 partition(under properties size is unknown). 
did ubuntu removed 2 partitions and made it into one?

second question is regarding drivers
what do I do about all the drivers? it seems to work fine but dont I need to install any drivers after installing ubuntu?(motherboard, sound card, video card, nic, etc...) 
except for the nvidia linux driver, i've never seen any linux drivers for other hardwares


P5W DH
7900GTX
onboard sound 
onboard nic
onboard wireless

thanks

p.s. sorry if these topic has been covered billion times already

---

### Post by Skrynesaver on 2007-05-13
Hi,
On the first point, if you selected use whole drive, then Ubuntu will have removed any existing partitions and created a root partition and a swap partition.
On the second point, the generic Linux kernel attempts to automatically load the apropriate modules (drivers) for any device it is asked to use.

---

### Post by Obor on 2007-05-13
Welcome to ubuntu :) 
This should give you a list of partitions (paste into terminal)
```
sudo fdisk -l
```

Nice thing about Ubuntu is that in most cases it "just works" so there is no need for drivers. The only drivers you might have to worry about is the graphix card and wireless (if they don't work properly)

If you go to System-Administration-Restricted drivers manager it should tell you if you need to install any extra drivers.

These two pages might be a useful reading
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
and obviously this forum... :)

---

