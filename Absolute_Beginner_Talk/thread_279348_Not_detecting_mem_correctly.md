---
title: "Not detecting mem correctly?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-17
Hey I have 1gb of ram (1024mb) and linux only detects 1010 in cpu info widgets and 1009 in uname -m. And when I type in uname -g it says I have 0, so i 'dont' have a gb of ram? lol 

Can someone explain please :D

---

### Post by gustolove on 2006-10-17
ram is faulty, a stick of 512 is likely a stick of 500-510...

with my gig of ram it is listed as 1004Mb :-(

---

### Post by WalmartSniperLX on 2006-10-17
In windows it detected it as 1024. So I dont know if this is because windows was just detecting the 'name' of the memory stick, or if this is a problem ](*,)

The only time I know of, inwhich memory will be detected as something lower, is when you have an onboard video device sharing some. In this case I dont.

---

### Post by gustolove on 2006-10-17
I believe windows may be rounding the memory to the closest whole ammount. how much does it say during POST (the black screen with lots of information before you choose windows or linux)

---

### Post by WalmartSniperLX on 2006-10-17
> **gustolove said:**
> I believe windows may be rounding the memory to the closest whole ammount. how much does it say during POST (the black screen with lots of information before you choose windows or linux)

Well I deleted windows :D a while back. I was getting full 1024mb readings in cpuz (in windows). I could check the boot up screen. :D 

Infact I should test cpuz now

EDIT: Ok i just ran cpuz in linux, and its reporting 1010mb of ram.

---

### Post by gustolove on 2006-10-17
yeah, so i'm guessing it was a case of windows lying to you!! :-P

---

### Post by WalmartSniperLX on 2006-10-17
> **gustolove said:**
> yeah, so i'm guessing it was a case of windows lying to you!! :-P

Dont think so :D  Because readings in cpuz are exact. Also when you buy ram you get EXACTLY what it is rated for. This is a problem with linux, or maybe just a problem with me understanding how linux manages ram.

Because when you buy 1GB you WILL get 1024MBs. 

Unlike HDDs, ram is rated in MegaBytes (MB) while HDDs are rated in Megabits (Mb). Maybe thats what you're thinking (in the first place) since when you buy a HDD that claims to be rated at 160gigs, it turns out less (because theyre sold/advertised in bits but reported on the pc as bytes). 

I dont know, but its an idea :D Maybe its buffers :-k

---

### Post by bodhi.zazen on 2006-10-17
> **WalmartSniperLX said:**
> Well I deleted windows :D a while back.


NICE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

No microsoft here either.

---

### Post by WalmartSniperLX on 2006-10-17
> **bodhi.zazen said:**
> NICE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

No microsoft here either.

^-^

---

### Post by ewl1217 on 2006-10-17
I'm no expert on the matter, but this is my understanding of it: 

The difference between the reported space and the actual memory size is the space that the kernel occupies. Unlike other programs the kernel absolutely can not be swapped out. As such, that portion of the RAM isn't reported.

---

### Post by gustolove on 2006-10-18
But have you checked in your BIOS or in the POST screen to see what ammount of RAM it says is there?

sorry if u listed it earlier but i didn't see it.

---

### Post by mcduck on 2006-10-18
IF I recall right, the kernel is loaded into memory when booting linux, and the space it uses is not calculated as available RAM when linux is running. So if you have 1024MB of RAM and your kernel image takes 14MB when loaded you only have 1010MB left..

IF you want to check that your memory is ok, there is the memtest option in Grub menu. LEave it running for couple of hours (or overnight) and if you get no errors you can be sure that there's nothing wron with your RAM.

---

### Post by WalmartSniperLX on 2006-10-18
> **gustolove said:**
> But have you checked in your BIOS or in the POST screen to see what ammount of RAM it says is there?

sorry if u listed it earlier but i didn't see it.

Its detecting 1024 :D I havnt posted this yet 8)

---

### Post by WalmartSniperLX on 2006-10-18
> **mcduck said:**
> IF I recall right, the kernel is loaded into memory when booting linux, and the space it uses is not calculated as available RAM when linux is running. So if you have 1024MB of RAM and your kernel image takes 14MB when loaded you only have 1010MB left..

IF you want to check that your memory is ok, there is the memtest option in Grub menu. LEave it running for couple of hours (or overnight) and if you get no errors you can be sure that there's nothing wron with your RAM.

Ok that makes sense. Someone else said this too so it must be it :D Ill run memtest tonight, overnight. Ill see how my mem stresses :D

---

