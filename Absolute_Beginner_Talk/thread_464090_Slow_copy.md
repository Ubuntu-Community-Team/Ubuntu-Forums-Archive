---
title: "Slow copy"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Balazs_noob on 2007-06-04
Hy guys

i have 2 Sata drives ( both samsung 200GB & 250GB )
copying between them is very slow ( 15mbyte/sec )
i tried copying with Krusader , Nautilus , Gnome commander

on windows XP i can copy with 45-50 mbyte/sec (Total Commander)

i'm using 7.04 Ubuntu Feisty Fawn

do i need some sata handling driver ???

ohh another problem :)
when i copy on linux is uses 90-100% CPU
windows only 40%

Thanks Balázs

---

### Post by Balazs_noob on 2007-06-04
no solution or tip anybody ???? :(

---

### Post by phr0ze on 2007-06-04
I don't know if this still applies but this sounds like a problem I used to see a lot in Windows. Again this is just a clue as I am not an expert but in windows it was a setting called DMA which had to be handled in device manager.  I'm sure this is also available somehow in linux, so please look for it.

With DMA off in windows you would see 100% CPU usage and drive operations would be very slow.

Again, I know your problem is Linux, so I hope searching for DMA will help you find a solution.

---

### Post by Balazs_noob on 2007-06-04
i haven't found nothing similar :(

but i think the problem is  linux dosn't support Sata properly out-of-box

thanks that you tried ;)

---

