---
title: "Delete Partition"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by TzaB on 2008-03-09
Hello all, i have a problem with the partition.
I have 3 partitions in my pc:

1. Windows XP
2. Ubuntu
3. Kubuntu

I want to delete the partition of Kubuntu and i want the size that has now the Kubuntu to add to Ubuntu Partition.
I read that this is possible and i read other posts in the forum with this problem but i cant find a solution.
So lets tell you which is the main problem.
I tried both Partition Magic and GParted programs but i have the problem that when i boot them, i see first the main screen of the programs and after 2 minutes my screen goes black and it appears a message that says the following:

Signal except limits
83kHz/60Hz

Have you got an idea on how to solve this?
Thanks for reading

---

### Post by bumanie on 2008-03-09
Not sure if I am right, but it looks as though your screen refresh rate is too high or too low. Try System -->  Preferences --> Screen Resolution and alter the Hz to within the limits specified (that is if they are outside the stated values). If the refresh rate doesn't seem to be the problem, I'm sorry, I can't suggest anything else at present.

---

### Post by Paqman on 2008-03-09
This is not the source of your error but don't forget that you can't modify a mounted partition. So run Gparted from a LiveCD if you want to change your main Ubuntu partition.

---

### Post by TzaB on 2008-03-09
I changed the resolution but the problem is remaining the same.
Thanks for your suggestion.

Paqman, i downloaded the iso GParted and then i burned it to a cd. Then i inserted the cd and boot the machine for the GParted cd.
This is the correct action right?

---

### Post by TzaB on 2008-03-09
I inserted the GParted CD to and old pc that i have and it was working fine. I did the same options to the pc that i have the problem but it doesnt want to work :/
If you have any ideas please post a reply.
Thanks

---

### Post by Paqman on 2008-03-10
> **TzaB said:**
> 
Paqman, i downloaded the iso GParted and then i burned it to a cd. Then i inserted the cd and boot the machine for the GParted cd.
This is the correct action right?

Absolutely, yes.

The problem sounds like your xserver (the bit that creates the graphical inteface) isn't configured properly. What happens if you try some of the different boot options (safe graphics mode, recover sessions, etc?) Even if all you're able to get is a command line it should be possible to fix your problem.

---

### Post by zvacet on 2008-03-10
If you can start and open Gparted live CD you will see option force......driver.Try select** vesa**.

---

