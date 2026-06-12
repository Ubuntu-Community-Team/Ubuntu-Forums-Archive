---
title: "Desktop Not Loading"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by tyrant5 on 2007-09-07
Lets see, where to begin.

I installed kubuntu 7.04 and everything was fine until I tried to do something beyond my skill level.

I tried to enable NTFS write/read with ntfs-3g and I got to a step that I could not get to work right. I can't find the site that I was using as a guide that day and am writing this from xp.

The error I got seemed to be a result of a wadcom entry written somewhere. When I deleted those entries of wadcom it messed up my kubuntu install.

Any ideas, where to start?

---

### Post by eapache on 2007-09-07
How exactly is it 'messed up'?

---

### Post by antisocialist on 2007-09-07
i have an idea where to start
instert kubuntu live cd in ur disk drive
turn on computer and go to boot menu
set boot first to cd-rom
save
start live cd
install
BAM! problem solved
o ya also install it on ur winxp computer as microsuck winblows is as good as 2 year old milk left on the counter (not a pretty sight)

---

### Post by tyrant5 on 2007-09-07
I'd like to fix it if possible, without having to redo the install.

And I'm not sure how it's messed up. Before I deleted the entries it'd boot up, now it won't.

I was deleting entries to xorg.conf regarding the wacom entries. I wish I had the links behind the actions. As in why I was doing these steps, but I can't find them.

---

### Post by eapache on 2007-09-08
Boot into recovery mode through grub, then type```
sudo nano /etc/X11/xorg.conf
```There are two wacom sections in xorg.conf, and you most likely only got one of them. There should be a bunch near your mouse/keyboard sections, and then some more at the very bottom under 'server layout'. delete them both and restart.

---

### Post by tyrant5 on 2007-09-08
Got it working again. 

Still having problems accessing my ntfs drives. It recognizes them both in the fstab, but only one of them is actually showing up. Not sure why.

edit; Got that problem fixed now too. Now I have to figure out what to do now..

---

