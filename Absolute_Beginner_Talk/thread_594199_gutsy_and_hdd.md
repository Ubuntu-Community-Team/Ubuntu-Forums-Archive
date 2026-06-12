---
title: "gutsy and hdd?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by hait2 on 2007-10-27
hi it's me again, with yet another newbie question =)

bg info: laptop inspiron 6400, some sort of sata hdd (if you can tell me where to find more detailed info, i will)

i've noticed that in ubuntu, whenever it's busy doing something (aka loading, like when i'm scrolling, alttabbing, loading a game, etc.) there's this short quiet screeching sound coming from hdd..

it's not present in windows (i dual boot) so i don't think my hdd is dying on me just yet
with googling the only thing i've found with respect to gutsy and hdd wasn't quite what i was looking for

(it told me to do hdparm -B 255 /dev/sda, which a) didn't fix the problem and b) wasn't the fix for my problem to begin with)

anyway i'm wondering what that noise is, is it a problem, why's it not present in windows and most importantly, how to disable it <3

thanks a lot in advance ^_^

---

### Post by hait2 on 2007-10-27
bump?:(

---

### Post by Daveth on 2007-10-28
found out a bit about this, but no expert in this field. 

It looks like hdparm is designed for disks other than SATA, which looks like standard install for this laptop model. The -B 255 flag you used turns off advanced power management according to this;

[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

It also suggests that it should be compiled from new for the kernel you have.

So, possibly the wrong command line program (there is a less advanced sdparm for SATA drives),  and advanced power management turned off. This may all be a red-herring, but I would get rid of that first and then see if the screeching goes away. As you note, if the drive was dying, it should die equally across both OS's, not just Ubuntu.

Anyway, a few thoughts. Hopefully others can chip in.

---

### Post by hait2 on 2007-10-28
well, i did reset the hdparm value back to its default (i was told from 2 different sources its 99 or its 80) so i tried them both, but obviously that didn't do anything with respect to the quiet screeching noise since it was default value to begin with

i took a look at sdparm as well, but, short of experimenting with all the flags (dangerous?), i didn't find anything that could help

anyone have any more ideas? even if it's not disabling the sound, but just telling me *what* it is would be extremely helpful

thanks in advance~

edit: i did find something related with respect to hdparm/sdparm/the noise i'm experiencing at 
[http://ubuntuforums.org/archive/index.php/t-394716.html](http://ubuntuforums.org/archive/index.php/t-394716.html)

i'm fairly certain the rotarychainsaw fellow was experiencing the same problem as me; unfortunately, it wasn't addressed in that thread..

ill keep googling

---

### Post by offroad64 on 2007-10-28
I also have the same issue. I don't think it is dying dive. I have 3 new Seagate drives and they do the same as discribed.:confused:

---

