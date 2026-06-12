---
title: "fix my grub"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2008-01-16
ive got 2 HD gutsy is on hda xp is on hdb. i can boot both by using Super Grub but i would like to fix this.
without using disk ubuntu mounts shows all linux but no windows, i just need to get the window option back to the grub. tried doing live CD to reinstall and go as far as step7. i dont want anther install of ubuntu. where do i go from here?

---

### Post by kellemes on 2008-01-16
Try adding this to your /boot/grub/menu.lst

```
title		Win
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

If it doesn't work try..

```
title		Win
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by gn2 on 2008-01-16
The answer is probably in here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by perixx on 2008-01-16
> The answer is probably in here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Yes, excellent guide that is! Perhpas of spcecial importance here is the 'map command' trick...

perixx

---

### Post by trucker33377 on 2008-01-17
> **kellemes said:**
> Try adding this to your /boot/grub/menu.lst

```
title		Win
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

If it doesn't work try..

```
title		Win
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Thanks I gave this a shot but Im not very good the the command line i get as far as 

grub>

and then i figure out how to input what you said to try. also just so its clear windows is on hdb. 

thanks i know ill get this fixed sooner or later

i should just take the time to learn the gimp and throw windows in the trash

---

### Post by perixx on 2008-01-17
AFAIK, Windows needs to have 'C:' environment as long as it's the only Windows among your system (that'd be 'hda' in Linux or 'hd0' in Grub). 

Since you're using 'hdb'/'hd1' (second HDD), you're gonna have to use the 'MAP'-trick, as described on the website mentioned above. Or you switch the boot-sequence in the BIOS, so Windows' HDD is the first device to boot from, every time you want to boot Windows - you're gonna have to switch it back for Linux, then, of course.

perixx

---

