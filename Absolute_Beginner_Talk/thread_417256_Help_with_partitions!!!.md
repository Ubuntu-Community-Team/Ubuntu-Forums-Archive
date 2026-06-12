---
title: "Help with partitions!!!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Reshuken on 2007-04-21
Ok guys I have a problem. I just installed Ubuntu on my computer, and it works like charm... BUT I partitioned my hard drive the wrong way: now my WinXP partition is only ~20GB but I wanted it the other way around. So is there anyway to make my WinXP partition bigger and shrink the one in Ubuntu? I have read about Gparted (or something similar), so do I have to use that program or is there some other way? Thanks in advance!!!

---

### Post by Happy_Man on 2007-04-21
Well, if you still have your LiveCD, you can boot from that again, and use the copy of Gparted on there to fix your partitions...

---

### Post by Reshuken on 2007-04-21
Ok, so I need to boot with the LiveCD again. I suposse I have to manually modify the partition table right? The thing is that I don't really want to mess my partitions, so I would like someone to explain me what do I have to do. I'm somewhat of a noob so any help is appreciated.

---

### Post by Reshuken on 2007-04-21
Ok, I boot again using the LiveCD, but I can't find Gparted anywhere. What do I have to do? Or is there some other way?

---

### Post by Happy_Man on 2007-04-21
I believe it is in the System menu, under the title GNOME partition editor.

---

### Post by rillip on 2007-04-21
It's a little hard to provide you direction without knowing what it is you're hoping to get.

In general, you'll want to shrink the partitions that are there and boost the one you want to be larger.  The swap partition is what the Windows paging file would be for, so be careful when adjusting it.  You won't break anything since you're on the live CD, but you don't want to make it too small or your system performace will suffer when you boot back up.  You want to leave some room on root too.  I would say at least eight gigs or so.  This is pretty much where the OS and packages are installed to, so you want to leave room for upgrades and such.  You can leave more or less room, depending on your drive situation, just be concious of how much room is free.  Letting it hit too high a disk usage is bad.  To give you an idea, my root hit 100% and there wasn't enough room to make the files neccessary for xserver to start.  Until I cleared some room, no GUI for me.  So give it as much as you want, and then watch the space and make sure it's not getting too full.  I've seen people set with 5.5GB and only have 1GB left, so my number is probably a bit conservative.

---

