---
title: "cinema display turns black"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by nbcmayhem on 2006-06-01
just dl the 6.06 desktop (ppc) iso, booted it with "live video=ofonly", the loading-graphics seemed to be somehow 8bit colors. after that my display turns black and the fans are at 180mph!

2x2,3ghz powermac g5 
ati x800xt mac edition
20" cinema display 

on my powerbook g4 ubuntu 6.06 is running like a kitty cat. 

some tricks to get 6.06 running on my G5 ?

---

### Post by rottenmac on 2006-06-01
[QUOTE=nbcmayhem]just dl the 6.06 desktop (ppc) iso, booted it with "live video=ofonly", the loading-graphics seemed to be somehow 8bit colors. after that my display turns black and the fans are at 180mph!

2x2,3ghz powermac g5 
ati x800xt mac edition
20" cinema display 

on my powerbook g4 ubuntu 6.06 is running like a kitty cat. 

some tricks to get 6.06 running on my G5 ?[/QUOTE]


I installed it on a separate drive, running a G4 / 450 and had no problems, but I can't actually RUN it. I wish i could be of more assistance, but it seems we are all S.O.L.

When I start up with the ATL down, i can choose it, but thats all.

---

### Post by digs on 2006-06-01
It's most likely a video issue. I had problems with using the default resolution on my LCD until I edited the xorg.conf file. With the desktop install try:

linux resolution=1024x768
vga=795
vga=775

If none work then the alternate install cd is your best bet.

---

### Post by CRiZ on 2006-06-01
i dont have a cinema screen
i have a iMac G5, but i have the same problem, i put the CD, and boot from it, then i type live and enter, the fan on my imac is going really fast, then the screen turns white, then black and it stays black, and the fans still running and i have to restart the pc :S

what can i do? :confused:

---

### Post by nbcmayhem on 2006-06-01
type

live video=ofonly

---

### Post by CRiZ on 2006-06-01
[QUOTE=nbcmayhem]type

live video=ofonly[/QUOTE]

i think i did, but i think i typed OFANLY, instead of ofOnly
let me boot my computer right now and do it again.

---

### Post by CRiZ on 2006-06-01
when i put 'live video=ofonly' then push enter, it takes me to a screen with the abuntu logo, and then it starts like doing some list check and everything its ok, but like at 75% of the list something says Failed its like 'pbbuttons' somthing like that, then after it says the failed thing by it, the screen turns black and a little line is flashin in the top left courner, then the screen turn all black (like if it was off) and the fans are going really fast

what should i do? ](*,) ](*,) ](*,) ](*,) ](*,)  :confused: :confused: :confused:

---

### Post by nbcmayhem on 2006-06-02
dunno, ubuntu is crap if it comes to new world macs.
ppc/mac support is poor, too.

---

