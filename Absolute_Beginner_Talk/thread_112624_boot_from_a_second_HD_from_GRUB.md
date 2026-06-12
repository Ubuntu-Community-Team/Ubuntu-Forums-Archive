---
title: "boot from a second HD from GRUB"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by kornmation on 2006-01-04
Well my case is that i got a compaq presario with 2HD, 1 HD with to partitions 1 NTFS for windows and second partition ext3 for Ubuntu and the second HD fat32 for win98 SE how can I set grub so i can load win98 from the second HD sow i can use my programing progrmas that are stuck in my second HD (the programas my friend gave them to me and i dont got the cd's)

---

### Post by taseal on 2006-01-04
i'm not sure if GRUB searches the 2nd HD for an OS to boot from

---

### Post by kornmation on 2006-01-04
soo what can i do????

---

### Post by taseal on 2006-01-04
good question lol

when u are setting up ubuntu, it doesnt find 98se OS I assume?

---

### Post by kornmation on 2006-01-04
nop it only found XP i tried to setup like it does in XP but when i try to boot it only stay in the screen and doesnt do anything 
grub setting for XP:
root (hd0,1)
makeactive
savedefault

i tried that and it doeint do any thing
like this

root (hd1,1)
makeactve
savedefault

and it frezes

---

### Post by Jukey on 2006-01-04
i dont' know. but did you try (hd 0,0)?

if it doesn't work sorry in advance.
i dont' really know anything about grub.

---

### Post by kornmation on 2006-01-04
the thing is that the hd that has win 98 is in IDE1 not IDE0 and i tried a lot of things, if there is any way that i could do anything it will help

---

### Post by piedamaro on 2006-01-04
title Windows XP
        map (hd0) (hd1)
        map (hd1) (hd0)
        rootnoverify (hd1,0)
        chainloader +1
        makeactive



This is what I use to boot xp on first partition 2nd harddisk. Good luck! ;)

---

### Post by kornmation on 2006-01-04
ok will that work on a win 98 SE

---

### Post by R3linquish3r on 2006-01-04
i got all that written, but when i try to save the file it says that it cannot write to the file......

for referense im using kate to edit it.

thx in advance

---

### Post by kornmation on 2006-01-04
hey an thanks it worked thanks a lot now i can use my progrmas again

---

### Post by piedamaro on 2006-01-04
R3linquish3r you have to gain root permissions to edit that file (and  many others).
Type:
sudo kate

from a terminal.

kornmation, you're welcome! ;)

---

