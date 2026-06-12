---
title: "[SOLVED] Made a mess with LVM!"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-01-26
Another 'I made a mess of...' thread!

I apologise in advance if I have started something without fully understanding it despite all the advice, but here goes.

I have two drives in my Ubuntu box. I have installed Ubuntu on a small partition and want to use the rest of that drive and the other for storage as a server. I wanted to be able to see it from XP as one large drive so from reading on here decided to go down the LVM route.

I followed [this]("http://ubuntuforums.org/showthread.php?t=555638&highlight=lvm") guide, which was very helpful and I think I understand most of it but I ran into a problem:

I started off thinking I would call my shared big drive 'media' -  did not check to see if this was already in use! Any way, I got to Step 2 of Formatting the LVM module and of course I am told that 'media' already exists.

I thought, no problem, Ill call it ,server, so went to Step 7 of install and setup to try and use lvcreate to recreate 'server', but as you might have guessed I am told that there are no extents available.

I don't really understand what an extent is but how can I delete the ones I have used and start again?

If I run gparted I can see that there is a new 'drive' in /dev/mapper/data-media. I assume I have to delete this but how?

Again, I know I should understand things before I rush on in but hey, you learn by your mistakes and there is no critical data on this machine!

---

### Post by Twizzle on 2008-01-26
Through a method of trial and error I managed to use lvremove /dev/data and it seems to have worked!

(knowing my luck I have deleted something important but hey - you live and learn!)

---

