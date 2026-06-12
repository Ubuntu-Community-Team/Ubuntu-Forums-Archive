---
title: "Problems with installation."
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by hongyu6868 on 2006-11-18
I need to do a dual boot. Can someone help me?

I cannot start it without safe gfx mode. It freezes if I start it normally. LiveCD runs perfectly. I clicked install, and at the partitioning part of it, it says, "Failure to create enough space". But I have 250GB Memory Left!

Please help!

I have Dapper Drake Version.

---

### Post by ewl1217 on 2006-11-18
Just a few questions here...

Did you do automatic or manual partitioning? If you did automatic partitioning, what option did you choose? If you did manual partitioning, how exactly did you do it?

Is there anything else on your hard drive that you wish to keep, or do you want to leave it all to Ubuntu?

---

### Post by turbojugend_gr on 2006-11-18
You need to be more specific, this way you will help other to help you.

If it freezes how can it run perfectly? I suppose you are using Ubuntu 6.06.1 Live CD?

What choice did you make when you were prompted for partioning?

How many disks do you have, do you have windows installed ? 

WHat exactly you wish to do partionwise, I mean hom many partiotions do you wish to create. And so on.

Plz make things a little more verbose, so you can recieve appropriatew help.

Best Regards, TJ.

EDIT: Ah! Beat me to it.

---

### Post by hongyu6868 on 2006-11-18
Okay, I did auto partitioning and allocated 50 GB. That is because I don't know how to do manual partitioning. Can you help me manually partition it? I tried many guides, including psychocats.net

EDIT: The safe gfx mode runs perfectly, but the normal startup freezes. Thats what I meant.

---

### Post by ewl1217 on 2006-11-18
If you enter manual partitioning and post a screenshot of the current partitioning scheme (or just type it all out), someone here may be able to help you through it.

---

### Post by hongyu6868 on 2006-11-18
Umm...

NTFS 42GB
Free Space 218GB

Rounded.

When I use free spcae to partition it has ext3's, linux-swaps, and more stuff

---

### Post by turbojugend_gr on 2006-11-18
Here's what I do:

1. I make up som free space according to my needs.

2. I make 3 partitions: "/" -> ext3 (anything more than 4 gigs is perfect) "/home" -> ext3 (whatever suits you, your personal space, I give it 50gbs, you may give 2gigs or whatever, that's where you store most of your staff) "swap" -> swap (2xyour RAM's size).

3. I format 'em, and go on.

I hope this helps, try using a guide along too though, so you can be more sure you do everything nice and neat.

---

