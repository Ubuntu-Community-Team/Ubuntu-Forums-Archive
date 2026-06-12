---
title: "Dual Bot Trouble"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-08-02
I re-installed windows, now i have windows XP running on my computer, It's the only OS. I put in Ubuntu 6.06 (the CD) and when the desktop loaded I double clicked the icon which says "Install". I entered the required information correctly, but when i got to step 5 (Prepare Disk Space). I have some problems... I want to resize IDE1 Master 160 GB 7200RPM Hard drive, but no matter how much space i select, either 51%, 100%, or what ever I get the same error which does not make sense because Ubuntu only takes up 2 gigs of space.

[IMG]http://http://img183.imageshack.us/img183/1998/failedgl3.png[/IMG]

(Error: Failed to create enough space for installation)

Someone please help!

---

### Post by ltk5 on 2007-08-02
You could also try to partition your drive by using Gparted, and skip the step 5. It comes in as a liveCD, and it 
can also be installed on an USB drive.

Before partitioning your drive, be sure to defragment it.

---

### Post by {A}Poly on 2007-08-02
> **ltk5 said:**
> You could also try to partition your drive by using Gparted, and skip the step 5. It comes in as a liveCD, and it 
can also be installed on an USB drive.

Before partitioning your drive, be sure to defragment it.

ok so I'll defragment in windows, then how do i use this Gparted. is there some command to use it or something?

---

### Post by {A}Poly on 2007-08-02
um.. bump

---

### Post by carloslosgrande on 2007-08-02
[FONT="Comic Sans MS"]You'll need to download, and burn, a copy from here;
> [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
and then use it to partition your disc as you want.
Its a live cd GUI, much like the ubuntu cd. That is, after you've burned it, reboot and it will load up and you can partition your unmounted discs (can't do that while they're mounted, ie in use.)
I find GParted very useful and have used it many times.[/FONT]

---

### Post by {A}Poly on 2007-08-02
so gparted-livecd-0.3.4-8.iso i save to disk or open with file roller? then i burn it onto a blank DVD and put it in the tray and reboot right?

---

### Post by carloslosgrande on 2007-08-02
[FONT="Comic Sans MS"]Burn it as an iso file, just like you did for the ubuntu live cd.
And you don't need to use a dvd disc for it, its not that big.
Yes, and then reboot and it will load up. Follow the instructions to the main partitioning screen and you can move and resize your partitions to your hearts content.
It would be a good idea to** [COLOR="Red"]back-up[/COLOR]** any files first[/FONT], including those on XP.

---

### Post by {A}Poly on 2007-08-02
I can't open my tray... it does not open. Porobably because ubuntu is running on the live CD right now or something.

---

### Post by bodhi.zazen on 2007-08-02
Ubuntu requires more then 2 Gb

You *should* make a swap, although it is not critical.

Swap size = RAM X2 up to 1 Gb max. If you have a laptop and use the hibernation feature swap = ram

Next you need some space for root, or /, or the partition where you will install Ubuntu.

I think the minimum is 3 Gb, perhaps 3.5 Gb. If you go that small you will likely run out of space quite soon. If possible I would advise 10-15 Gb.

========

You can not eject the Ubuntu CD when you are running live. Other live CD's load into RAM and will allow this, but not Ubuntu.

You can probably partition with the Ubutnu CD, open a terminal and type :

```
gksu gparted
```

You need to unmount a partition before you can resize it ...

---

