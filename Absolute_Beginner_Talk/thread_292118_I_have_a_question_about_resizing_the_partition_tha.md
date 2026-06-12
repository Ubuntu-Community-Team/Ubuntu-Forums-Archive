---
title: "I have a question about resizing the partition that has Dapper on it."
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by sktfeelsdapper on 2006-11-03
I have 2 hd's hda that has dapper on, and hdb.

To make a long story short, for some reason or another an extra 7.8 gb's were showing up on the end of my main partition, which i safely deleted and rebooted (system is still here, obviously :D ) but now I was wondering if it was possible for me to resize hda for more linux space.

Obviously you can't in gparted because you can't unmount it, also every single live cd i have does not work in this computer. I had to netboot (lin4win) in order to actually get an installation to work (my cd drive i think is completely borked, lesson of the story don't buy from craigslist).

So is there another way around this without using the livecd or do i just have to make do with my 10gb hd and the crappy space i have now?

Any help?

You can also email me at [email]shyguyfrenzy@gmail.com[/email], which I would prefer because it takes a bit for people to answer on here.

---

### Post by CatKiller on 2006-11-03
You could rip out the other hard drive and put it in a computer that **can** boot from the cd. Or is running Linux. And use GParted. That's probably what I'd do.

---

### Post by sktfeelsdapper on 2006-11-03
While that would seem logical my (sudo) aptitude for computers is very little to none.

hmmm well, i guess i'll stick to putting everything on my other hd and just using the main one for programs.

---

### Post by CatKiller on 2006-11-03
You can still partition the free space and mount the new partition wherever you wish in the filesystem tree. It's not like you have to waste the space.

---

