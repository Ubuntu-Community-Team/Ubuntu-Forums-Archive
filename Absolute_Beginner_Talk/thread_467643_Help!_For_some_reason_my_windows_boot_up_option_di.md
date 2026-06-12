---
title: "Help! For some reason my windows boot up option disappeared!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Lordcoca on 2007-06-07
I was messing around in ubuntu earlier and the software update option came up and so naturally, I updated everything. When I rebooted, I noticed that the windows option was gone. What happened and how can I fix this?

I also installed the startup manager program so I could make the windows option the default. But when I ran it I noticed there was no windows option in there either?

---

### Post by Bohlio on 2007-06-07
check and see if you still have your windows partition, ```
df -Th
```

Then check and see if you have an entry like this at the bottom of your /boot/grub/menu.lst
```

title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I think you may just be able to add this in order to add the windows partition to the list. Someone please correct me if I am wrong. Replace Windows XP Media Center Edition with whatever your OS version is, and replace (hd0,1) with the location of your windows partition. The numbering starts at zero, so hd0 stands for Hard Drive 1, and the 1 stands for partition 2. If your windows partition is /dev/sda1, you would type (hd0,0) If it is /dev/sdb3, you would type (hd1,2)

---

### Post by PointSource on 2007-06-07
Then, you probably need to insert something like this into /boot/grub/menu.lst:

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

[http://www.tuxmachines.org/node/16701](http://www.tuxmachines.org/node/16701)

---

