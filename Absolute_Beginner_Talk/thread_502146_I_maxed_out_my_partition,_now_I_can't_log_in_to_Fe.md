---
title: "I maxed out my partition, now I can't log in to Feisty Fawn."
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by clipse on 2007-07-16
How can I get in to delete some stuff out. 

thanks, 

clipse

---

### Post by phr0ze on 2007-07-16
Boot the Live CD and use it to manage your drive.

---

### Post by clipse on 2007-07-16
It says I don't have permission......obviously I'm still new to all this. :)

---

### Post by davidjmayo on 2007-07-16
can you remember how/what you did to "max out the partition"?

What partition?

---

### Post by clipse on 2007-07-16
Two things. I was downloading an iso for Helix and I did a backup. I did allocate a large partition. A window came up saying I was running low on memory (I stupidly thought it meant RAM) so I stopped for the day. The next day I went to get on the computer and it says I didn't have room to write a log or some such thing. 

clipse

---

### Post by bodhi.zazen on 2007-07-16
You can :

1. boot to hard drive, select recovery mode. This will give you a command line interface but you will be able to delete things.



2. Boot the live CD, mount your hard drive partition at say /mnt :

```
sudo mount /dev/hdxy /mnt
```

The delete with nautilus : ```
sudo gksu nautilus /mnt
```



[list][*]Either way, bo not forget to empty the trash, both for your user and root.[/list]

---

