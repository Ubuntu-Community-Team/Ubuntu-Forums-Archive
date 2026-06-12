---
title: "installing ram hardware in an ubuntu box"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-12-11
i am curious, what are the steps involved in installing new ram upgrades in an  ubuntu machine? 
i have an acer 5610z laptop with 1 gb of ram that can be upgraded to four gigs using 2-2gig so-dimm chips.  the computer still runs circles around windows vista with 1 gig, but i would like to add more, because i multi task a lot and i want a lot of elbow room.

thanks

---

### Post by umattu on 2007-12-11
Install the hardware and turn on the power.

---

### Post by OldTimeTech on 2007-12-11
When I upgraded my ram in my significant other's Acer Laptop, Ubuntu just saw it and it worked.  Of course it's a dual core intel and so I am running ubuntu 64 on it.

---

### Post by FuturePilot on 2007-12-11
You shouldn't really have to do anything. Just shut the computer down, disconnect the power, install the RAM, hook everything back up, and turn it on. Should just work :)

---

### Post by thebestofall007 on 2007-12-11
its that easy? thanks, ive never installed ram in a computer b4.  ive used computers, but never owned one before . (THIS ACER MACHINE IS THE FIRST I HAVE EVER OWNED).

---

### Post by thebestofall007 on 2007-12-11
to oldtimetech, why would a person need ubuntu 64 on a dual core? mines a dual core and it works AWESOME on both cores.

---

### Post by Steveway on 2007-12-11
But you should keep in mind that Ubuntu nor Windows can use the full 4GB if you only have a 32bit-processor or use a 32-bit Operating-System.
So if either one of the above is true for you then you would have wasted some money.
At leas for Linux there is a workaround on 32bit-Systems. You'll have to compile a kernel with bigmem-support, this will be a bit slower but you'll be able to utilise youre full 4GB.
If you have a 64bit processor and run a 64bit Operating-System then go ahead and put that RAM in.

---

### Post by plucky on 2007-12-11
[indent]Don't laptops use swap file to hibernate to disk?[/indent]

Increase swapfile to reflect increase in memory

---

