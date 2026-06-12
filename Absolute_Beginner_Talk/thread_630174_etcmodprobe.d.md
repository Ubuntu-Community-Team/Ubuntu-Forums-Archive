---
title: "/etc/modprobe.d"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-03
so i was redoing the cables in my computer[rearanging them to allow for better airflow, dusting components and such]
and i had everything but the drives out of the case
i am ruling out static shock as a possible factor, as i have a grounding strap, and my floor is tile
to get to the point, when i booted up, it droped the splash screen and said```
warning filesystem hda/hd1 has been mounted 39 times without being checked; forcing check now
checking......................................................39%
warning: bad line in /etc/modprobe.d line 8        ignoring with SUDO
warning: bad line in /etc/modprobe.d line 9        ignoring with SUDO
warning: bad line in /etc/modprobe.d line 10      ignoring with SUDO
warning: bad line in /etc/modprobe.d line 11      ignoring with SUDO
checking....................................................100%

warning: bad line in /etc/modprobe.d line 8        ignoring with SUDO
 warning: bad line in /etc/modprobe.d line 9        ignoring with SUDO
warning: bad line in /etc/modprobe.d line 10      ignoring with SUDO
 warning: bad line in /etc/modprobe.d line 11      ignoring with SUDO

warning: bad line in /etc/modprobe.d line 8        ignoring with SUDO
 warning: bad line in /etc/modprobe.d line 9        ignoring with SUDO
warning: bad line in /etc/modprobe.d line 10      ignoring with SUDO
 warning: bad line in /etc/modprobe.d line 11      ignoring with SUDO

warning: bad line in /etc/modprobe.d line 8        ignoring with SUDO
 warning: bad line in /etc/modprobe.d line 9        ignoring with SUDO
warning: bad line in /etc/modprobe.d line 10      ignoring with SUDO
 warning: bad line in /etc/modprobe.d line 11      ignoring with SUDO

mounting file systems
starting up...

```

can anyone tell me what this is about?
this is mostly from memory, the FSCK took a good 5 minutes, if it is relevent, i have moved the PCI devices around
i had my nvidia on the bottom most slot, i moved it to the top slot, and the network card is now in the middle, with sound card on the bottom
i also modified my IDE cables that are flats, they are now "rounded", i just curled them and taped them
if anything here would cause this, or is this normal linux/unix behavior?

---

### Post by spiderbatdad on 2007-12-03
every 30 mounts, Ubuntu checks the file system. It looks like there is a bad line of code in your modprobe.d, which seems a little strange since it's a directory of files. Anyway, seems like your os handled it and loaded?

---

### Post by 99bluefoxx on 2007-12-03
yes, fortunately, it did start up. i was worried and excited at the same time, i was thinking that if it had died on me, i would start up from cd, and salvaged my files, then reinstalled, windows first[i want certane softwares that wont work with WINE, lol] then put linux back in
lol
i guess its good that  that it mounted though, ide rather backup to a second harddisk but all my extras are burned out[one failed, one click-of-deathed, the other was badly formatted halfway through a OS installation]
thanks for the help=3

---

