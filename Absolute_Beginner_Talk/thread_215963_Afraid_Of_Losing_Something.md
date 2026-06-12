---
title: "Afraid Of Losing Something"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by saintxaero on 2006-07-14
I was wondering if anything on the drives that are listed will be reformated or can i go along with the install. I provided a screenshot, could anyone tell me?

---

### Post by Jagot on 2006-07-14
The only one that will be formatted is the / partition.  The others should be left as they are.  You should be able to go ahead - but of course you have backed up everything important to you, right?

---

### Post by Kobalt on 2006-07-14
Your post is not quite clear... What exactly do you want to do ? Format your hda3 partition ? 
On your screenshot only hda3 is selected for a formatting so I don't see any reasons why other partitions should be damaged. 
But a backup never caused any damage so you might want to save a few precious things maybe...

---

### Post by saintxaero on 2006-07-14
i just want to make sure that the only one that will have something lost on it will be the hda3 part that i'm fiddling with.

---

### Post by orb9220 on 2006-07-14
Where is your swap partition? You need to create one

---

### Post by saintxaero on 2006-07-14
can i put that on any drive without having it reformatted?

---

### Post by coffeecat on 2006-07-14
Ignore - duplicate comment to one just made.

---

### Post by saintxaero on 2006-07-14
> **coffeecat said:**
> You don't appear to have allocated or set up a swap partition. Is that what you intended?

can i set a swap partition on any drive and it not be reformatted or am i doomed?

---

### Post by Jagot on 2006-07-14
You don't have to have a swap partition but it's advisable unless you have lots of RAM - you do not need to reformat anything - just resize one of the other partitions and use the freed space - your swap space should be approximately twice the size of your RAM.

---

### Post by saintxaero on 2006-07-14
> **Jagot said:**
> You don't have to have a swap partition but it's advisable unless you have lots of RAM - you do not need to reformat anything - just resize one of the other partitions and use the freed space - your swap space should be approximately twice the size of your RAM.

so if i have a gig of ram i should setup a 2 gig swap?

---

### Post by Jagot on 2006-07-14
It really depends on what you're doing and whether it will use the swap space.  With 1 gig you really shouldn't need a 2 gig swap.  The rule about twice the RAM is really relevant more to systems with lower RAM.  I've some people witha gig of RAM running with 512 swap fine.

---

### Post by Madpilot on 2006-07-14
With a gig or more, swap is optional, from what I've both experienced & read.

I've got 1Gb, never set up swap when I set up this harddrive, and given that I hardly ever max out my RAM usage, can't really see the use of swap.

---

