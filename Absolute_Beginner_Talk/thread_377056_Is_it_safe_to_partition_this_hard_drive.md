---
title: "Is it safe to partition this hard drive?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-03-05
Ok, so i want to partition my hard drive so i can run XP and Ubuntu. I was told that i need to  defrag it so all of the stuff on the drive is on one side of the drive, or else the stuff on the distant side of the drive will get deleted.

[IMG]http://yorktown.cbe.wwu.edu/07Winter/sayerj/images/defrag.GIF[/IMG]

This is my hard drive. I have those two green lines on the right, which are not movable because they are in use. I imagine they contain all my windows OS files and such. I have tried to move them in safe mode, and they refuse to. 

Is this volume safe to partition using gparted in the dapper liveCD?

ALSO: I am trying to back up this drive onto an external hard drive. I was just copy and pasting the drive... But it wasn't working.

It wouldn't let me since I have so many files that are in use. 

Can I access my C drive in the liveCD so i can backup my hard drive before partitioning it?

---

### Post by mikewhatever on 2007-03-05
Those are unmovable files, probably page.sys (page file). You can't move them while Windows is running, because Windows uses them. Gparted should be able to do it, as well as Diskeeper Trial Version through boot time defragmentation.

---

