---
title: "Blank screen on Powermac G4 with ubuntu 12.04"
date: 2012-09-24
forum: Apple Hardware Users
---

### Post by ryanvade on 2012-09-24
Hello everybody. i am having problems with running ubuntu on my powermac g4. The powermac g4 has 2 graphics cards which are both ati. it has 1.5 gb of ram and a 553 Mhz dual power cpu. The install went fine but it won't show anything after rebooting. If I connect a monitor to the pci card I see this:
```
 done
copying OF device tree...
Building dt strings...
Building dt structure...
Device tree strings 0x02cf9000 -> 0x02cf9c7f
Device tree struct  0x02cfa000 -> 0x02d1f000
Calling quiesce...
returning from prom_init
_

```Any thoughts on what I should do?

---

### Post by ryanvade on 2012-09-24
I tried ```
[FONT=Courier New]video=offb:off[/FONT]
``` and it said ```
done
found display  : /pci@f2000000/ATY,RADEONp@12,opening... _
```

---

### Post by miguelbaines on 2012-09-25
I was having the same problem today, but i still can't get this thing to boot completely.

Here's what I did to hopefully help you move forward -

Use the CD to edit the yaboot.conf and change -

append="queit splash" to append="video=ofonly" you'll have two, I changed both.

cmd x
y
enter
ybin -v
exit
reinstall yaboot
reboot system

See what happens.

---

### Post by ryanvade on 2012-09-27
Could you explain how to use the cd to repair yaboot. I assume you mean to use the rescue mode. 
I used ```
[FONT=Courier New]nouveau.modeset=0[/FONT]
```[FONT=Courier New] and got this. but the menu didn't look as nice as they do now.[/FONT]
[IMG]http://i1251.photobucket.com/albums/hh555/ryanvade/Screenshotfrom2012-09-24214241.png[/IMG]

---

