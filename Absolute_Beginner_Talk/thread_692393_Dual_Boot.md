---
title: "Dual Boot"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Brantis on 2008-02-09
I have recently (12 hours ago) reinstalled Ubuntu 7.10 on this computer.
Now I am unable to dual boot into XP which is on a second HD and is slave.

I have went into menu.lst and made an addition to the bottom that looks like this

# Booting Into Windows XP From Slave Drive
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

The problem is that whenever I make this selection and hit Enter, I get an "ERROR 13" (I dont remember all that it says) and it pretty much forces me to go back and make another selection.

It is worth noting that last time I had Ubuntu installed I did have a different entry in the Grub menu. but I honestly don't think that it is much of a difference because I have tried both of them.

---------Old Grub Entry----------

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

-------End Old Grub Entry--------

Any help would be appreciated.
Nothing has changed on the Slave drive so I am not sure what gives.

---

### Post by jan quark on 2008-02-09
I somewhere have seen that changing this
> 
title Windows XP
root (hd1,0)

to that

> title Windows XP
root (hd0,0)

helped
but please I am guessing and I really do not remember well
so try this at your own risk

but it would be cool if it helps
:)

---

### Post by spiderbatdad on 2008-02-09
maybe try **rootnoverify**

---

### Post by Brantis on 2008-02-09
try using rootnoverify instead of what I have in there right now?
Of should I put this at the end of the string

---

### Post by spiderbatdad on 2008-02-09
in place of what you have now.  **rootnoverify (hd0,1)**

---

### Post by Brantis on 2008-02-09
Error 12: Invalid Device Requested...

That is what I get whenever I try to boot..
After changing above mentioned setting.

---

### Post by spiderbatdad on 2008-02-09
i believe what you want is what you have posted above as "old grub entry" except root (hda0,1) or rootnoverify (hda0,1)

---

### Post by Aurora@FleetBuzz on 2008-02-09
Perhaps a suggestion in this thread will help?  Good luck.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by R@inm@n on 2008-02-09
> **Brantis said:**
> I have recently (12 hours ago) reinstalled Ubuntu 7.10 on this computer.
Now I am unable to dual boot into XP which is on a second HD and is slave.

I have went into menu.lst and made an addition to the bottom that looks like this

# Booting Into Windows XP From Slave Drive
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

The problem is that whenever I make this selection and hit Enter, I get an "ERROR 13" (I dont remember all that it says) and it pretty much forces me to go back and make another selection.

It is worth noting that last time I had Ubuntu installed I did have a different entry in the Grub menu. but I honestly don't think that it is much of a difference because I have tried both of them.

---------Old Grub Entry----------

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

-------End Old Grub Entry--------

Any help would be appreciated.
Nothing has changed on the Slave drive so I am not sure what gives.



This is what I have on my dual Ubuntu/Win xp dual boot, in /boot/grub/menu.lst


 title                windows XP
root                (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader    +1



This goes at the end.

 Also, while you are in there, change the lines: hidden to #hidden and adjust the display menu time to 10 secs.

Save and quit settings.



   HTH,


   R.

---

### Post by Brantis on 2008-02-10
Yep....

Ok, the problem is that somehow I managed to format over the slave...

I noticed this whenever I tried to look through the other HD and came across the other working boot information. lol 

This is why its not very smart to play around with partitioning and formatting when you haven't had a good nights sleep in about a month..

---

### Post by bumanie on 2008-02-10
Go to here and look up your error code numbers. This is probably the definitive grub site on the internet. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
There is a section marked grub errors about half down the page (it's a long page).

---

