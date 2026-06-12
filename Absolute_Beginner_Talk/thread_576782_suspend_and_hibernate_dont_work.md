---
title: "suspend and hibernate dont work"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-15
for some reason suspend and hibernate arnt working  on my laptop all it does is look like it is doing somthing and then it will go to a blank screen with a little bar at the top of the screen as if you are going to type:confused:

if anyone can help?.....

---

### Post by Pumalite on 2007-10-15
Laptop? What's the size of your /swap?RAM?

---

### Post by Bliepo32 on 2007-10-15
And what kind of motherboard do you have? I once had a motherboard which (for some weird reason) completely disabled this.

---

### Post by kamitsukai on 2007-10-15
well i have 1gig ram and 2gig swap and im not sure how to find out what type of motherboard i have is there some kind of command i can try?

---

### Post by kamitsukai on 2007-10-15
o found a command

```
sudo lshw -html > hw.htm
```

and this is what it says about my motherboard
```
id:	
core
description: 	Motherboard
product: 	CANYON-Intel ODEM
vendor: 	MTC
physical id: 	
0
version: 	FAB-3
serial: 	12345678
slot: 	DC Input
```

---

### Post by bliffle on 2007-10-15
What kind of laptop?

---

### Post by kamitsukai on 2007-10-15
i believe it is a cusom build by novatech (second hand)

---

### Post by kamitsukai on 2007-10-15
LOL maybe i wont get this sorted for 2morrow :P i cant find any info on this motherboard on google....

---

### Post by Dorv on 2007-10-27
I'm having the same problem with my Gutsy install.  I have a fresh install on my HP dv5000, and I can't hibernate.  What do I need to tell everyone to get help :)

---

