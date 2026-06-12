---
title: "New memory, Ubuntu near death..."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-09-13
I added an extra stick of memory.  The first time I tried to boot Ubuntu it failed, the second it ran some check and then restarted.  Then I got the desktop with some icons changed and no programs working.  Plus a load of error pop ups. Now unusable.  

Windows XP on the other hand recognises the new memory and works fine. 


I'm getting pretty close to ditching Ubuntu, every little thing causes hiccups.

---

### Post by startherepodcast on 2007-09-13
In Grub, you know the menu after switching your computer on showing Ubuntu...blabla and Ubuntu ..blabla..recovery

Select Memory Test there and see what happens. Maybe the new RAM broke while being shipped?

---

### Post by anaconda on 2007-09-13
yep, maybe the new ram is broken, or incompatible with the old ram, or of wrong type.

---

### Post by justleen on 2007-09-13
> **startherepodcast said:**
> In Grub, you know the menu after switching your computer on showing Ubuntu...blabla and Ubuntu ..blabla..recovery

Select Memory Test there and see what happens. Maybe the new RAM broke while being shipped?

It works in wondiws, so little chance of that failing...



When your booted the  not-working-very-well-Unbuntu, can you manage to get into a console?

---

### Post by aberadam on 2007-09-13
No terminal.  No programs work in the Ubuntu desktop now. 

It ran through a check at start up and came up with a fail, something like" fcdsk fail exit 3"

The memory's working fine in XP so far.  Shows up as being there and everything working normally.

---

### Post by aberadam on 2007-09-13
fcdsk died with error status exit 3

---

### Post by aberadam on 2007-09-13
Just took the memory out, Ubuntu's working again.

---

### Post by tszanon on 2007-09-13
> **aberadam said:**
> No terminal.  No programs work in the Ubuntu desktop now. 

It ran through a check at start up and came up with a fail, something like" fcdsk fail exit 3"

The memory's working fine in XP so far.  Shows up as being there and everything working normally.
Just because the hardware works fine in Windows, it doesn't mean it's not defective. My broken mouse proves it. :)
I suggest running MemTest. Let it run for at least 1 full pass. If you're "lucky", it's defective hardware. Just replace it and everything will be fine again.

I also suggest removing the new memory and checking if the problem persists, then putting it back.
If the problem vanishes when you're not using the new memory, then it's very likely to be the problem.

---

### Post by aberadam on 2007-09-13
OK, I'll run the test.

---

### Post by justleen on 2007-09-13
> **tszanon said:**
> Just because the hardware works fine in Windows, it doesn't mean it's not defective. My broken mouse proves it. :)
I .


there quite a bit of difference between a mem module or a mouse...

True, windows seems to tolerate more errors, when it comes to broken hardware.. (i had some probs with a partition table, winodws booted, but not *nux)

---

### Post by aberadam on 2007-09-13
Ahh, I'm an idiot, after checking the mobo manual it was in the wrong slot.  Ubuntu works fine now.  Sorry for wasting your time... 

I think I'm supposed to have dual channel memory now that I have two 1gb sticks, but it still says "single channel" at startup.  Any ideas how to enable dual channel?  I couldn't find anything that seemed relevant in BIOS.

---

### Post by maniac_X on 2007-09-13
> **aberadam said:**
> 
I think I'm supposed to have dual channel memory now that I have two 1gb sticks, but it still says "single channel" at startup.  Any ideas how to enable dual channel?  I couldn't find anything that seemed relevant in BIOS.

check your mobo manual or mobo makers website for details on that. it may be that the mobo manufacturer only suggests certain tested brands of memory to gaurantee duel channel....or at least matching pairs of sticks(same brand). some mobos can be very picky.

---

### Post by aberadam on 2007-09-13
These are different brands, one bought 18 months after the other, one's got bigger chips on it than the other.  Not much chance they're matched.  There's nothing in the manual about it.  Ahh well, don't suppose it makes much difference.

---

### Post by maniac_X on 2007-09-13
If they are as you say unmatched sticks, then that is most likely the reason you are not getting duel channel  mode proper. 

does your system still recognize total ram from both sticks?

also , what is the brand and model # of your mobo?

---

### Post by aberadam on 2007-09-13
It's Gigabyte, GA-K8NMF-9.  It recognises the extra memory, just says it's in single channel 64 bit mode at the beginning.

---

### Post by maniac_X on 2007-09-14
...according to the manual:
```
Duel Channel DDR
GA-K8NF-9 supports the Duel Channel Technolgy...etc etc
Channel A: DDR1, DDR3
Channel B: DDR 2, DDR4

If you want to operate the duel channel technology, please note the following explanations 
die to the limitation of the nVidia chipset.

1. Dual Channel memory cannot be used if one DDR memory module is installed.
2. If two DDR memory modules are installed (same storage capacity), one must be added to
 a channelA slot and theother in a Channel B slot in order t use dual channel memory. You 
can simply install the memory moduels into slots of the same color but we recommend slotting 
them into DDR1 and DDR2.
Duel Channel Memory cannot function if both DDR memory modules are installed on the same 
channel.

3. If four DDR memory modules are installed, please use memory of the same storage capacity
 in order to use dual channel memory and for BIOS to detect all the DDR memory modules.
```

Now you know how to set up Duel Channel. :)

Bad news is though that you probably need a matched pair of sticks. Here's a link to Newegg.com with a selection that would work for your machine.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170147%201052107965%201052407862%201052308477%204027&bop=And&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170147%201052107965%201052407862%201052308477%204027&bop=And&Order=PRICE)

---

