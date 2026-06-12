---
title: "RAID 0 and Ubuntu"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by gsnider@nyc.rr.com on 2006-06-10
Hi to all
As a complete beginner to Linux and Ubuntu I need help with finding out from those who have tried whether I can install Ubuntu on my machine which is set up with RAID 0.
If possible could you reply via e-mail to [email]gsnider@nyc.rr.com[/email] thanks.

---

### Post by Nikusan on 2006-06-12
[QUOTE=gsnider@nyc.rr.com]Hi to all
As a complete beginner to Linux and Ubuntu I need help with finding out from those who have tried whether I can install Ubuntu on my machine which is set up with RAID 0.
If possible could you reply via e-mail to [email]gsnider@nyc.rr.com[/email] thanks.[/QUOTE]

[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by wombat20 on 2006-06-18
Would be nice if the wiki was updated for Dapper, as it is close to useless in its current form.

---

### Post by wombat20 on 2006-06-20
What it doesn't tell you and I think it should, is that you need to create swap and /boot paritions outside the RAID0 partition.  Also, you can't easily dual boot with only a RAID setup.  I used a separate single IDE disk for Windows.

I managed to make it work by making a 2GB swap on one HD and a 2GB /boot on the other, then using the remaining space as equal sized RAID partitions.  Granted 2GB is probably excessively big for /boot, but I wanted to keep them the same.  

Perhaps someone who understands this better than me could clarify this for others?  It would be good to have a proper walk-thru HOWTO.  Maybe this is not well explained in the wiki as it's mainly a server thing and most server users are more able?

---

