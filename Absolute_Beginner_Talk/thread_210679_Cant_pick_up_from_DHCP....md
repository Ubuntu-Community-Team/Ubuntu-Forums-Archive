---
title: "Cant pick up from DHCP..."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by mit on 2006-07-07
So, i have paritioned my drive and installed 6.06 :) 

eth0 is set to pick up from DHCP and displays the correct information within general, DNS and hosts but will not receive an address. Interestingly, i set a static IP to overide it and can ping my gateway but no further.
The other bizarre thing is, even though i set it back to DHCP it displays the static IP when i click on the icon at the top of the desktop and i can use NS Lookup.

Any ideas?

mit

---

### Post by ovimunt on 2006-07-07
Ok, easy, is your eth0 a wireless device?

If so, the solution is a bit more complicated. Thing is actually that it's not a real solution but more like fudging it a bit.

---

### Post by mit on 2006-07-07
Hi,

eth0 is wired
eth1 is wireless. 

I am trying to get the wired connection (eth0) working at the moment.

Thanks 
mit

Edit;

the strange thing is the default gateway device option won't stay on what you set it to once you close the box...

---

### Post by ovimunt on 2006-07-07
Fortunately my wired connection worked "out of the box" so I didn't need to even touch the settings there. Hence unfortunately I'm not sure what you can do about your problem with the wired connection. Sorry

---

### Post by mit on 2006-07-07
Sorted it. I disabled and re-enabled and it picked up an address :KS 

Maybe a glitch on ISA's behalf....

Mit

---

