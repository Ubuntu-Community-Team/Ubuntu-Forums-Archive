---
title: "2nd hard disc problem..."
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-09-06
As title really.  I have 2 hard discs in my machine - 1 with Ubuntu on, and one with XP on.  All my music is on my XP one, and i can ususally see it when im in Ubuntu if i go to places/my computer.  I turned my machine on today, went into ubuntu, but cant see the XP disc?

Any ideas?

Cheers. Alex.

---

### Post by Harpoon on 2007-09-06
There are two quick things to try first.  Run sudo fdisk -l and look to see if the drive with xp shows up.  If not, then got to places and navigate to /etc/fstab (or, while you are in the terminal, type gedit /etc/fstab) and look to make sure that drive is still included in the list.  If it is in the list, but not mounted, you can try sudo mount -a and see if that gets the drive up and running.

Otherwise, the most obvious thing to question is whether the drive, itself is functioning properly (did a cable come loose, for example).  

Gotta run, but try the no cost approach first.

---

### Post by aj5string on 2007-09-07
OK... i did the first thing, and i can see both my discs there.  I know that they are both working as one has Ubuntu installed, and the other has XP installed, and I have used both over the last day.

Just gonna try a couple of other things, and then get back to you!

---

### Post by aj5string on 2007-09-07
Right - i sorted it!  The issue was with Ubuntu seeing my XP hard-disc (cos it has all my music on it).  Turns out, the problem was that the last time i used XP it hadn't shut down properly (lol) - i tried one of the things suggested by Harpoon and it told me this.  So, booted XP, made sure it shut down properly - and all is good!

---

