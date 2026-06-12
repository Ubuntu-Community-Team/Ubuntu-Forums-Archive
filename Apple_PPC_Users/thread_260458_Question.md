---
title: "Question"
date: 2006-09-18
forum: Apple PPC Users
---

### Post by sbentzen on 2006-09-18
How much space does the swap partition need to be?

---

### Post by foolsh on 2006-09-18
no more than 4 gigabytes if the kernel supports memory swaping that big mine is set to 2 gigabytes more than enough for what i do 
not less than 256 megabytes though

---

### Post by ncappel1 on 2006-09-18
according to "the illustrated dual boot website" ([http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)) 1 gb should be enough, I put it at 3 because my friend told me to do so (and I trust him!). Maybe on the next install (on a possibly new computer) I'll make it a different size.

---

### Post by 3rdalbum on 2006-09-19
Ouch... 3 gigabytes of swap space!

For measure:

When I had 256 megs of RAM, Ubuntu suggested 600 megs of swap, but it only seemed to use 50, 60 megs of it. Now I've got 1.25 gigs installed in my computer, and Ubuntu rarely uses any of the swap (18 megs, tops, and I have no idea why it was using even that much).

The general rule is the same as Mac OS: 1.5x your installed memory, but no more than 512 megs.

---

### Post by ncappel1 on 2006-09-19
So is having 3 gigs adversely affecting the system? or is it just being inefficiant?

---

### Post by moore.bryan on 2006-09-19
*i've had some of the same questions and it was explained to me this way: swap is "spill-over" space for ram; that is, when there is a need to use more ram, but you don't have any more, linux uses harddisk space as virtual ram.  the caveat is that hd-ram is ssssssssssssslow, so it is only going to be able to use a small portion of it.*

---

### Post by sbentzen on 2006-09-19
so in a way you are saying that there really isn't a need for the swap partition or that you don't need alot? and i think this should be put into the directory of knowledge for newer users like myself.

---

### Post by moore.bryan on 2006-09-19
*i've read posts saying there's no need for it and those arguing for large swaps... when i was new, not long ago, i thought more swap=faster system.  that's not the case.  so long as you have "enough" swap, there's never a problem.  somewhere in these forums, there's a post which advocates a mathematical equation to figure out the best swap size for you... best advice: keep it sane.*

---

### Post by sbentzen on 2006-09-19
Thank you, Question answered.

---

### Post by 3rdalbum on 2006-09-20
Having a swap partition is a good idea. It's faster than a swap file.

Having a large amount of swap doesn't have adverse effects, and it doesn't make your computer faster... it's just a huge waste of space as most of it won't be used.

I'll just correct something I said earlier. When I had 256 megs of RAM in my computer, there were times when Linux was using 200 megs of swap, but for normal tasks it used much less.

---

