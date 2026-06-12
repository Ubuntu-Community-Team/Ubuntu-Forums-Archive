---
title: "FF install.  Stuck at step 4 out of 7"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-05-09
Firstly, TIA.  I'm trying to install FF as a dual boot with XP home on my Dell desktop.  I'm stuck as what to do on step 4 of 7 on the install.  

What do I pick for "how do you want to partition the disk?"

[LIST]
[*]Guided - resize SCS13 (0
[/LIST]
[LIST]
[*]0
[/LIST][LIST]
[*]0)
[/LIST]
[LIST]
[*]partition #1 (sda) and used free space
[/LIST]
[LIST]
[*]Guided - use entire disk
[/LIST]
[INDENT][LIST]
[*]SCS13 (0
[/LIST]
[LIST]
[*]0
[/LIST][LIST]
[*]0) (SDA) - 160.0 GB ATA ST3160812AS
[/LIST][/INDENT]
[LIST]
[*]Manual
[/LIST]

Sorry, that I'm such a nube. I have to admit that this is giving me horrible college flashback memories to Pasqual.

---

### Post by LaRoza on 2007-05-09
If you want the easiest method, shrinking xp and automatically install Ubuntu to the freed space, move the slider to the size you want and press enter.

XP should be defragged first.

---

### Post by ammmom on 2007-05-09
>  If you want the easiest method, shrinking xp and automatically install Ubuntu to the freed space, move the slider to the size you want and press enter.

XP should be defragged first.

okay, I defragged xp last night.  

This is going to sound really stupid, but what slider? Do I move back off of step 4 of 7?

TIA

---

### Post by LaRoza on 2007-05-09
No, it should be on the same screen, something like "resize and use freed space"

---

### Post by Sef on 2007-05-09
Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") for how to dual boot with the Desktop (Live) CD.

---

### Post by ammmom on 2007-05-09
I've totally effed this up. Install is telling my that I need a root directory and gives me a prepare partitions screen.

/dev/sda
/dev/sda1     ext 3    /media/sda1      156897 mb 3900 mb
/dev/sda5     swap                            3100    mb       0 mb

---

### Post by Sef on 2007-05-09
> I've totally effed this up. Install is telling my that I need a root directory and gives me a prepare partitions screen.

/dev/sda
/dev/sda1 ext 3 /media/sda1 156897 mb 3900 mb
/dev/sda5 swap 3100 mb 0 mb

I don't think so.

In /dev/sda, just put a /.   that will be set up as root.

---

### Post by ammmom on 2007-05-09
> I don't think so.

In /dev/sda, just put a /. that will be set up as root.
I'm sorry, can you break that down? If I right click on /dev/sda, I'm given the option to "new partition table" or "undo changes to partitions"

I don't understand how or where to put "a /."

Please tell me this gets easier.  I'm usually on a fast learning curve.

TIA

---

