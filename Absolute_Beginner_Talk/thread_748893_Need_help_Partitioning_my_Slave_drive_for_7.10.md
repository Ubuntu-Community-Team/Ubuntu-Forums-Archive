---
title: "Need help Partitioning my Slave drive for 7.10"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by randell6564 on 2008-04-07
Hello folks!
Been a long time since I've used Ubuntu/Linux, so I have forgotten how to do many things.

I have a 120Gig Master that houses Windoze, and a 20Gig Slave that is just waiting for Ubuntu 7.10.
My question is, What would be the best way to partition my 20Gig in order to get the best performance from Ubuntu?
Thanks!

---

### Post by Inxsible on 2008-04-07
There a lots of configuration that can work for you.
You can put both OSes on the same drive and then use the other solely as a shared partition between both of them.

But if 20 Gigs is all you want Ubuntu to have, then make sure you have at least 5GB for the root partition, 1 GB of swap and you can make the rest as home - 14 GB

Ubuntu can also read and write to NTFS partitions, so you shouldn't have a problem accessing the 120Gig drive from Ubuntu.

---

### Post by ant2ne on 2008-04-07
I'll argue that. I'd go with 10gig Root, 9gig home (or less), 1 gig swap. User data often takes less space than that even. How much RAM do you use. More than x2 your RAM is a waste of swap (imo).

---

### Post by randell6564 on 2008-04-07
> **Inxsible said:**
> There a lots of configuration that can work for you.
You can put both OSes on the same drive and then use the other solely as a shared partition between both of them.

But if 20 Gigs is all you want Ubuntu to have, then make sure you have at least 5GB for the root partition, 1 GB of swap and you can make the rest as home - 14 GB

Ubuntu can also read and write to NTFS partitions, so you shouldn't have a problem accessing the 120Gig drive from Ubuntu.
That was fast, thanks 'Inxsible'!
Now it's starting to come back to me.  I know that I COULD have used my 20gig for storage, shared by both OS's, but at this point, it's too late.  I would have to wipe, and reinstall, and I'm not in the mood for that for the time being. lol!  I will however do it eventually, and this time, Ubuntu will have the 120gig drive.
> make sure you have at least 5GB for the root partition, 1 GB of swap and you can make the rest as home - 14 GB
Thank you!  I use to just allow Ubuntu to partition the drive for me.  But this time, I Want to intervene, and attempt to get the best performance possible given my hardware. 
:popcorn:

---

### Post by randell6564 on 2008-04-07
> **ant2ne said:**
> I'll argue that. I'd go with 10gig Root, 9gig home (or less), 1 gig swap. User data often takes less space than that even. How much RAM do you use. More than x2 your RAM is a waste of swap (imo).
I'm a bit embarrassed to say that I only have 1Gig of Ram.  Not sure that I understand what you mean by:> More than x2 your RAM is a waste of swap.

---

### Post by Inxsible on 2008-04-07
There is a thumb of rule that says you should have a swap size that is twice the size of your RAM. But that rule doesn't hold good once your swap is 1GB (IMO)

If you have a swap of more than 1 GB, i just think its a waste of hard disk space.

---

### Post by randell6564 on 2008-04-07
> **Inxsible said:**
> There is a thumb of rule that says you should have a swap size that is twice the size of your RAM. But that rule doesn't hold good once your swap is 1GB (IMO)

If you have a swap of more than 1 GB, i just think its a waste of hard disk space.
Hmmm.,Interesting.  Thank you my friend!  I'm on my way!

---

### Post by Inxsible on 2008-04-07
> **randell6564 said:**
> Hmmm.,Interesting.  Thank you my friend!  I'm on my way!
Good Luck installing !!

---

### Post by randell6564 on 2008-04-08
> **Inxsible said:**
> Good Luck installing !!
Will post the results!

---

### Post by ant2ne on 2008-04-09
I got 8 Gigs or RAM and only 4 gigs of swap. I figured if I ever use 8 gigs of RAM, I'm going to need some swap. My last machine had 1Gig of ram and 2 Gigs of Swap. I have a laptop with 2 Gigs of RAM and 1 Gig of Swap.

I also like that linux allows one to control how often you swap. what is it, vmswappiness? or something.

---

