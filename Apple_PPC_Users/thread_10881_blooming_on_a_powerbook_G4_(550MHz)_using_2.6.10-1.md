---
title: "blooming on a powerbook G4 (550MHz) using 2.6.10-1 (hoary)"
date: 2005-01-12
forum: Apple PPC Users
---

### Post by jarlev on 2005-01-12
When I use F1 (to dimm brightness) on my powerbook G4 (550MHz), I get lcd blooming (screen 'seems' to melt). This happens with kernel 2.6.10, it does not happen on 2.6.9. Have anyone seen similar? The same blooming will occur after a lid close/open.

---

### Post by jarlev on 2005-01-12
also the command 'fblevel 0', gives blooming

---

### Post by chele on 2005-01-12
I have the same powerbook, and it does not happen here.

---

### Post by jarlev on 2005-01-13
[QUOTE=chele]I have the same powerbook, and it does not happen here.[/QUOTE]
Thanks for the information. After reading your post, I tried another way of installing. First I installed macosx 10.3.4. Using the macosx installer I splitted the 20G disk in two. My plan was to install Ubuntu on the second. Macosx installation went fine, ubuntu installation went fine. Then I added the hoary repositories and installed linux-image-2.6.10-1-powerpc. Now the blooming problem was gone. I don't understand why. Maybe macosx 10.3.4 installation did something that relates. Or maybe it's because this time I did not do a apt-get dist-upgrade to hoary. I run warthy, with 2.6.10 kernel from hoary repositories. The reason I use 2.6.10 kernel is that I don't have airport wireless on this powerbook, so I use a 3com pccard for wireless instead. This 3com card is supported in 2.6.10 and also sleep, with a pccard inserted, seems to work better on this kernel.

---

### Post by jarlev on 2005-01-13
Hm, I got the blooming back, it seems something gets corrupted when sleep/wakeup fails. Power recycle, makes the fixes the blooming problem until next sleep/wakeup failure. I'll now do a apt-get dist-upgrade to hoary.

---

### Post by jarlev on 2005-01-13
[QUOTE=jarlev]Hm, I got the blooming back, it seems something gets corrupted when sleep/wakeup fails. Power recycle, makes the fixes the blooming problem until next sleep/wakeup failure. I'll now do a apt-get dist-upgrade to hoary.[/QUOTE]
 When I use fn+F1 (to dimm) the lcd screen get darker and darker, and finally turns black (off). I I use 'fblevel 0', it'll bloom :(. 'fblevel off' don't affect the screen at all. I'm now running kernel 2.6.10-2-powerpc, dist-upgraded to hoary.

When, the bloom happens, I can get out of it by pressing fn+F2, which raises the fblevel to '1'

---

### Post by jarlev on 2005-01-13
[QUOTE=jarlev]When I use fn+F1 (to dimm) the lcd screen get darker and darker, and finally turns black (off). I I use 'fblevel 0', it'll bloom :(. 'fblevel off' don't affect the screen at all. I'm now running kernel 2.6.10-2-powerpc, dist-upgraded to hoary.

When, the bloom happens, I can get out of it by pressing fn+F2, which raises the fblevel to '1'[/QUOTE]
 the fblevel binary comes from a package called powerbook-utils. I removed it. The machine go nicely to sleep without it. Sleep/wakeup seems to work better now. I'll report back if blooming happens again.

---

### Post by jarlev on 2005-01-16
[QUOTE=jarlev]the fblevel binary comes from a package called powerbook-utils. I removed it. The machine go nicely to sleep without it. Sleep/wakeup seems to work better now. I'll report back if blooming happens again.[/QUOTE]
 ok, now I start to see some patterns.

I installed powerbook-utils again. I made no difference. After wakup the machine's lcd bloom's. But then I removed my 3com pccard, and now I have not had blooming since. I will run without pccard for some weeks, and then try to install the pccard again, to see if wakeup triggers blooming againg. 

fblevel 0 gives blooming, with and without the pccard. But fn-F1 down to 0 (lcd off), does not.

---

