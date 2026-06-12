---
title: "Macbook 5,5 not booting 10.10 from CD"
date: 2011-01-26
forum: Apple Hardware Users
---

### Post by Tokiopop on 2011-01-26
I have a freshly burnt 10.10 (64 bit) disc, which I know works (tried it on a Sony laptop, worked fine). When I try boot in on my Macbook (either by holding alt or through rEFIt), it will start, but it never finishes. 

In both rEFIt and when holding alt there are two new options with the disc inserted; a boot option, and a boot EFI option. When I choose the normal boot the animation of the dots lighting up just keeps repeating, and when I choose the other option, it brings me to a menu asking if I want to try Ubuntu or install it. This ends up just getting stuck after a few lines of text (not sure what they say, but if it's important I can go and check).

Sorry for the noobiness, the last time I used Ubuntu it was on 8. something, and I rarely use Linux except for in virtual machines (I'd like to change that :KS)

Is this known to not work, or am I doing it wrong? 

Thanks!

Edit: Also, I'm going to be installing this on my Macbook tomorrow when I get my new hard drive, so really this is just getting it to work so that I can install it.

Edit 2: What would be a good size for my swap partition if I have 4GB of RAM?

---

### Post by Tokiopop on 2011-01-27
If I press escape something along the lines of

/init line 7: can't open /dev/sdb: No medium found

This is working on a non-apple laptop.

---

### Post by rtyb on 2011-01-30
You don't need a swap partition with 4gbs of ram. 4's fine.

Just an advice:  Be sure to mount / and /home on different partitions, considering Ubuntu on Mac record...

And Ubuntu 64-Bit is just pure problem. Go with the 32-bot, easier, same stuff..

---

### Post by vuarnet on 2011-03-22
this worked for me: [http://ubuntuforums.org/showthread.php?t=1549174](http://ubuntuforums.org/showthread.php?t=1549174)

It's tricky, and risky... but if you're running OS 10.6.x, then that could be the problem. When I say risky, I mean make LOTS of backups. Then backups of your backups. Because when you downgrade grub, you are essentially deleting your bootloader and then replacing it. 

If you mess up during that stage, you'll be left with an unbootable mac. You would need to recovery using a retail install disk of Mac OS X then do a time machine restore to get back to where you were.

I'm currently typing this from my beautifully-working 64-bit 10.10 on my macbook ... so it IS possible, albeit a little nerve-wracking...

---

