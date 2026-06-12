---
title: "How come ??? Hdd mounting thing..."
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by kurniawands on 2006-07-25
:-k  guys,

first time i was installing dapper, i can't even see what's in my windows partitions since they are ntfs.... but then i decide to clean up and re-install everything...

first is dapper, and xp after, but i can't see the OS selection table when i was booting my pc, so i decide to re-install dapper again, it was all done.

i log in to my dapper, then i amazed that both of my hdd is there on my desktop... even i can access them.. (read only)... fyi, i haven't mount them yet. both hdd is still ntfs as my first installation... how come ??? since i then install dapper on other pc and my thinkpad... it wasn't done like that...

anybody can tell me something ???

ps: even when i see my fps rate is 3 times higher now... no glitch or anything like that. i'm using ati 9200 pro 128 mb and i haven't change the driver yet. it's still read mesa on the my glxinfo.... how come ???

---

### Post by orb9220 on 2006-07-25
If you install xp after dapper then xp writes to the mbr wiping any grub loader that is installed by linux. XP thinks its the only OS in the universe.

But when you install dapper after xp then it sees the xp allows for a dual boot system when it writes the grub to the mbr.

---

