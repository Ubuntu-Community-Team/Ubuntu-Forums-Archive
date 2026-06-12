---
title: "[SOLVED] Changing Swap size."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-06-08
Hi.
I recently installed Kubuntu on a 60gig drive.
I partitioned 25 gig for the OS and 5 gig for swap.
The remainder is for future use.
Ummm... I have a 1ghz Athlon and 768 meg of mem...
I feel that I dont need so much swap. Am I correct?
How can I adjust that smaller, of course, without losing data...

Whaddya think?;)

---

### Post by Bohlio on 2007-06-08
Im pretty sure you can, I think your swap partition gets re-written when you boot up again, I dont think any info stays there. but i could be wrong. If your swap partition is after your ext3 partition, then once you shrink it, It will add the empty space to the rest on your drive. But if it is before your ext3 partition, then you cant really make any use out of the freed up space unless you make another small partition in between. I think you cant expand partitions to the left, only to the right.

Oh, and i think your swap is supposed to be twice the size of your RAM, so in your case, you'd need 1536MN, thats only 1.5 GB.

---

### Post by baracuda68 on 2007-06-08
> **Bohlio said:**
> Im pretty sure you can, I think your swap partition gets re-written when you boot up again, I dont think any info stays there. but i could be wrong. If your swap partition is after your ext3 partition, then once you shrink it, It will add the empty space to the rest on your drive. But if it is before your ext3 partition, then you cant really make any use out of the freed up space unless you make another small partition in between. I think you cant expand partitions to the left, only to the right.

Oh, and i think your swap is supposed to be twice the size of your RAM, so in your case, you'd need 1536MN, thats only 1.5 GB.

Would I use the Kubuntu live CD? or Gpart?..( or is there a Kpart?)

---

### Post by drowner on 2007-06-08
yes you would need to use a liveCD because you won't be able to repartition a partition that is currently in use.

Either livecd is fine, or you can use a gParted live cd itself.

---

### Post by Bohlio on 2007-06-08
I've never partitioned other than manually doing it to dual boot ubuntu and XP but i think you can just run the live cd that you used to install ubuntu. Then in the terminal type in ```
gparted
```

Lol, I just tried it out to confirm and this message came up.
> Since GParted can be a weapon of mass destruction only root may run it.
Lol, I love comical error messages :-P
So... you need to run ```
gksudo gparted
```

---

### Post by baracuda68 on 2007-06-09
Thanks all!
The Gparted Live CD worked perfect!

Great advice!
thx

Bob

---

