---
title: "A bit too hasty..."
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by PhysicsGeek on 2006-03-25
Hello there--- I'm discovering that I might have rushed into Ubuntu. My old Windows system was completely ribald with viruses, etc, so I just completely wiped the harddrive and installed Ubuntu.

Now I've found myself in a situation where I need some Windows programs again (think *games*). Sadly, I've proved myself too inept to install Winex or whatever it is that runs Windows programs on Linux, so I'm trying to look into how to partition my harddrive now that Ubuntu is already the only OS.

Forgive me if these questions have come up before-- any advice for a total n00b on either partitioning or Winex?

---

### Post by djheadley on 2006-03-25
Your best bet is to back up any data you just can't live without because  Windows has to be installed first.  You can use a LiveCD to repartition the drive or, like I did, use a Windows or DOS startup disk to repartition and go from there. What Windows games are you missing?

---

### Post by Panhead Bill on 2006-03-25
Couldn't you just add a second hard drive to use for windows?  That way you could keep bill the gates locked inside the D drive.  (C*mpU$a has a 80 Gig drive on sale this week for $9.99 after rebate - sale ends tomorrow I believe)

---

### Post by krusbjorn on 2006-03-25
[QUOTE=djheadley]Your best bet is to back up any data you just can't live without because  Windows has to be installed first.  You can use a LiveCD to repartition the drive or, like I did, use a Windows or DOS startup disk to repartition and go from there. What Windows games are you missing?[/QUOTE]

Actually, Windows doesnt have to be installed first. If you resize your Ubuntu partition(s) in a partition editor (gparted for example), you can let the Windows installer make an ntfs partition on the unallocated space you just created. However, I think people has had problem with Windows taking over the MBR and having to reinstall GRUB because of that. I always had Windows on a separate disk so I never experienced those problems.

As a side note, I have been able to play any Windows games I have tried in Cedega. It's cheap and quite easy to use.

---

### Post by trorion on 2006-03-25
What games are you playing?  I'm looking for a reason to keep my windows partition now that I quit WoW...

---

