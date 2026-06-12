---
title: "internet connection w/three operating systems"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by bigb1ke on 2006-06-23
Helo All,
I'm a old MS retread, I've tried other versions of linux in the past but gave up and went back to windows. I loaded ubuntu 6.06 by accident (I needed 5.10 to support a program I wanted to try) I thought I'ed died and gone to heaven with ub 6.06. To make a long story short, here's my question/problem. I'm using a computer that had been loaned to friend who has dialup.  when I got it back I reinstalled my D-link DWI-G520 PCI adapter per instructions (using XP) several times because XP can't find it. In the mean time I loaded Ub 6.06 and without doing anything I found I was connected to the internet, through my router & internet service. Then I installed Ub 5.10. I now have XP, Ub6.06 & Ub5.10 running ok. Now to the problem.......
Ub 6.06 connects to the internet (I'm sending this using Ub6.06) and still can't get XP to use the G-520 (it does know it's there.) And Ub5.10 which I still need to use to support EMC2 doesent appear to know the G-520 there or I just don't know what to tell it so it can connect.  what now
Paul/bigb1ke](*,)

---

### Post by Apple 101 on 2006-06-23
For your wireless card, go to the D-Link site in 6.06 and download the Windows drivers from the support section.  Load them in Windows and get that working.  For your wireless card in Ubuntu, you can probably use ndiswrapper - it worked for my connection.  [This link]("http://forums.tuxtalk.org/index.php?topic=270.0") should help you get it running.  It's for another card, but it works fine.

For your other problem, check to see whether the programme you need from 5.10 is available in 6.06.

---

