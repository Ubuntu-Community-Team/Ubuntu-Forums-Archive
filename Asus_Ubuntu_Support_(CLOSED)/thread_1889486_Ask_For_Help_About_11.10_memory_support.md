---
title: "Ask For Help About 11.10 memory support"
date: 2011-12-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by letter2u on 2011-12-01
Hello there, I'm using ubuntu 11.10 64-bit on my asus 1015b notebook,
so now, i would like to upgrade my RAM to 2GB, how to check what kind of RAM that 11.10 would support?
and how much RAM that 11.10 64-bit could read?

sorry for my bad english translation.. :)

---

### Post by r_mano on 2011-12-02
It's not an operating system problem --- it's a hardware one. 
Linux would happily use the ram you put on your laptop, I have a 1005P working great with 2G ram (the maximum --- hardware-limited) for my netbook.

---

### Post by letter2u on 2011-12-03
> **r_mano said:**
> It's not an operating system problem --- it's a hardware one. 
Linux would happily use the ram you put on your laptop, I have a 1005P working great with 2G ram (the maximum --- hardware-limited) for my netbook.

well, thanks for the answer dude :)

but, as I see on the other thread, there's some problem with ubuntu that didn't recognize the memory change, any idea about it?

---

### Post by r_mano on 2011-12-03
Could you link the other thread? These kind of problem are very rare, and very machine-specific.

---

### Post by letter2u on 2011-12-03
> **r_mano said:**
> Could you link the other thread? These kind of problem are very rare, and very machine-specific.

here is the link: [http://ubuntuforums.org/showthread.php?t=905752](http://ubuntuforums.org/showthread.php?t=905752)

as i saw there, ubuntu didn't recognize the new memory that have been changed

---

### Post by r_mano on 2011-12-04
If you read the thread, there where two problems there: 

1) memory not recognized by the Vaio-something laptop --- hardware problem because the BIOS did not reported it (so nor Linux nor any other SO will recognize it). 

2) another poster telling that 32-bit Linux use a maximum of 4G of RAM (*), normal and known --- use 64 bit if you have more RAM.

(*) I know, there is highmem and PAE mode etc etc, but they are not recommended solution. 

So if you buy your extra GB for your eeePC, chances are that you will have your new RAM recognized without any problem, as it happened for me.

---

### Post by letter2u on 2011-12-04
> **r_mano said:**
> If you read the thread, there where two problems there: 

1) memory not recognized by the Vaio-something laptop --- hardware problem because the BIOS did not reported it (so nor Linux nor any other SO will recognize it). 

2) another poster telling that 32-bit Linux use a maximum of 4G of RAM (*), normal and known --- use 64 bit if you have more RAM.

(*) I know, there is highmem and PAE mode etc etc, but they are not recommended solution. 

So if you buy your extra GB for your eeePC, chances are that you will have your new RAM recognized without any problem, as it happened for me.

now I get it! :D
thanks dude! it help me a lot :)

---

