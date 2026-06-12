---
title: "Live CD + Wine + Warcraft 3"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Jexel on 2007-09-26
I was wondering what is the fastest way to create a live cd/dvd that contains wine and warcraft 3. It doesn't necessarily need to be ubuntu it can be any other distro. I just require a fast simple way of doing it. Does anybody know?

Thanks a lot.

---

### Post by Lord Illidan on 2007-09-26
It's called reconstructor, check it out here : [http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1](http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1)

---

### Post by sunexplodes on 2007-09-26
It would be pretty much unplayable, though. Running an entire OS off a CD is slow as hell, adding a game to that would be SLOWWWWW.

---

### Post by Jexel on 2007-09-26
not really, we've had lan nights at our uni and we run starcraft off a live cd and it ran just fine. However...warcraft 3 will be significantly more expensive to run but...we shall see

---

### Post by Lord Illidan on 2007-09-26
If you have enough RAM, and make the livecd as small as possible, it can be very playable. Let's face it, all you need is wine, and Warcraft 3 itself, you don't even need GNOME!

Make sure you put in the nvidia drivers, of course.

---

### Post by dn_desaku on 2007-09-26
If you have an extra FAT32 partition, here's my advice. 
Make sure the FAT32 partition is a good size (2~5 GB)

[LIST]
[*]Download and Burn SLAX Kill Bill ([http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/SLAX-KillBill-Edition-1957.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/SLAX-KillBill-Edition-1957.shtml) or from the official site [http://www.slax.org/download.php](http://www.slax.org/download.php))
[*]Run it as a Live CD
[*]now login
[*]then type in 'help'
[*]look for a command that creates swap files
[*]enter that command and make the swap file **[SIZE="5"]HUGE[/size]** 
[*]about 2~3 GB depending on how powerful Warcraft is
[*]Then:
[*]```
startx
```
[*]Insert the Game CD.
[*]Run the game Setup
[*]The option should appear in the KDE Start Menu >Wine>Warcraft (or something like that)
[*] If all goes well it should run. 
Also, if you want make a configfile for SLAX so you would have all settings restored when you use SLAX agian. 
[/LIST]

Sorry I could not give all the complete code. I haven't used it in a long time :lolflag:

---

### Post by Jexel on 2007-09-28
I download Slax Popcorn edition and through the use of MySlax I can incorporate Wine, however, how can I incorporate Warcraft 3 onto the disk itself?

---

