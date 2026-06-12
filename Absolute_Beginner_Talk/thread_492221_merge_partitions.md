---
title: "merge partitions?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Bubs on 2007-07-04
Is there a way to merge an unallocated partition into an existing partition?

---

### Post by mlentink on 2007-07-04
No. But you can increase the size of one partition at the cost of another, which is essentially the same thing

---

### Post by Bubs on 2007-07-04
how?
 I tried to do that by booting up the feisty live cd then going to the "gnome partition editor"  and all I could do is make the partitions smaller.  not bigger...  I'm not used to messing with parttions so i'm kinda lost on this.

I have a partition thats 15g that I was going to setup for a duel boot, but I don't want to duel boot anymore so I wanted to "merge" that 15gig back into "/home" or even "/"

  and I don't want to mess up the partiton I already have.  it took me a while to get setup like I want it and I would hate to have to do it again.

thanks

---

### Post by smoker on 2007-07-04
hi, download and use the 'gparted live-cd', it has never failed me.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

i've had problems with the fiesty gparted, so i don't use it at all now, though that might just be my ineptitude!

---

### Post by davidjmayo on 2007-07-04
> hi, download and use the 'gparted live-cd', it has never failed me.

I'll second that--never caused me any problems. Of course a backup would be wise just in case

All you need to do is move the partitions left or right into the free space depends where it is, and again etc 
click on the partition to move not the free space . The arrows resize the partion and I think there's a move in the menu or it's right click to select move (sorry don't remember)

I would use apply after each step though, not do a lot then  apply

---

### Post by Bubs on 2007-07-10
cool thanks for the replies.  It worked.  turnes out what was confusing was that I had a swap partition between the one I wanted to grow and the unallocated space.  I didn't realize that I needed to delete that before I tried to grow the other partition, then add the swap after that.

thanks people for the help + link

---

