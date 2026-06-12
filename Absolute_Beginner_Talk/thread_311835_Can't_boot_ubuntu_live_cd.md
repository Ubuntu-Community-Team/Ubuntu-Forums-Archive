---
title: "Can't boot ubuntu live cd"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Xochipilli on 2006-12-03
Hey,

a friend of me recomended ubuntu as a new OS.
He said that I should first try a live cd to see if I like it with no chance of screwing up my notebook.
He gave me a ubuntu live cd version 5.10 for your PC.
Now I changed my bootorder so that the cd-drive was on top of the bootorder. Now when I restart my notebook with the ubuntu live cd in the drive, he just loads very long, but then eventually starts windows xp, but everything runs very slowly.
I thougt that maybe the problem was the cd, so I burned a 6.06.1 live cd myself, and tried a official 6.06 LTS and none of them would work (they work on my dad's computer).

Is there anyone who can help me with this problem, because I can't fix it, and my friend also doesn't know whats wrong. The CDdrive works normally on windows so I don't think its broke or something.

My notebook is a hp pavilion pentium 4 3,2 Ghz with 1 Ghz DDR2, 100 Gb Harddisc space, A Radeon x600 mobility. And the cd drive is a DVD R/RW burner with an unknown speed to me.
Could this be some compatibility problem or something.

I hope this will soon get solved,
Greetings,
Peter R.
Belgium

---

### Post by taurus on 2006-12-03
How fast did you burn it?  Some laptops (even desktops) have problems reading a fast burning CD so if you can, try to burn it at 4x.

---

### Post by Forceflow on 2006-12-03
Checked the MD5 hashes before you burned it ?

---

### Post by Xochipilli on 2006-12-03
I checked the hashes, but I burned it at full speed.

But I also tried 2 official ubuntu live cd's (from the local linux supplier), versions 6.06 LTS for your PC and 5.10 for your PC, and none of them works, but they work on my friend's notebook and on my dad's PC.

---

### Post by Xochipilli on 2006-12-04
so nobody knows the what could be the source of the problem?

---

### Post by LLRNR on 2006-12-04
It happened to me once, I can't remember if it was an Ubuntu CD or something else, but I only managed to boot from the CD after - as you said - I changed  the boot order **and** temporarily disabled the boot off the HDD.

HTH,

LLRNR

---

### Post by rajeev1204 on 2006-12-04
hi

is it possible that after downloading ,instead of burning a cd image he burned it as as data cd?? lol cos i did that the first time !!

so u put the cd in drive and what happens? it boots into windows.i again burned it as image file and then everythhing was fine 


regards

rajeev

---

### Post by Xochipilli on 2006-12-07
> **LLRNR said:**
>  I changed  the boot order **and** temporarily disabled the boot off the HDD.


Hey, thanks, you where right, I just had to disible the HDD boot.
Now I can boot the Live cd.

---

