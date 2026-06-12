---
title: "Kids games  RI-LI anyone know how to install this?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-01-05
Hi,
Looking for some games for my 4 year old.
RI-LI from the ubuntu games list looks just the job, except i've not got past the download page yet.  (  [http://doc.gwos.org/index.php/Children_Games](http://doc.gwos.org/index.php/Children_Games)  ) Anyone know which version i need to download

- RPM Versions :

    * Ri-li-2.0.0-1.i586.rpm size: 18.7Mo (19 611 266)
    * Ri-li-2.0.0-1.src.rpm size: 13.2Mo (13 791 918)
    * All Debian versions [http://packages.debian.org/unstable/games/ri-li](http://packages.debian.org/unstable/games/ri-li)
    * For Ubuntu an 'Alien' tutorial in Frensh to install Ri-li.

I don't read French (or frensh) unfortunately... Dutch, German or English and i'd be fine ;)

Any Ubuntu gamers out there with 5 minutes to spare - for a few tips on how i do this?

Would be very much appreciated.

---

### Post by kane77 on 2007-01-05
If they arent in repositories (neither universe nor multiverse) you should go for the debian package... Download it. You will have .deb file in location where firefox saves downloads.
Find it and double click it and the gdebi manager will take care of the rest...

in case of unmet dependencies error you should locate the needed packages, preferably on packages.ubuntu.com or packages.debian.org...

---

### Post by stoer on 2007-01-05
Thanks for the quick reply, 
said 4 yr old is just about to eat  so i'll give a go after he's finnished.
Cheers.

---

### Post by stoer on 2007-01-05
Ok, chose for the deb packet.
Got sent through to the download section and see the following...

Other Packages Related to ri-li
[dep]= depends	[rec]= recommends	[sug]= suggests

    *

      [dep] libc0.1 (>= 2.3.5-1) [kfreebsd-i386]
          GNU C Library: Shared libraries

    *

      [dep] libc6 (>= 2.3.5-1) [not alpha, i386, ia64, kfreebsd-i386]
          GNU C Library: Shared libraries
      libc6 (>= 2.3.6-6) [i386]

    *

      [dep] libc6.1 (>= 2.3.5-1) [alpha, ia64]
          GNU C Library: Shared libraries

    *

      [dep] libgcc1 (>= 1:4.1.1-12) [not hppa, m68k]
          GCC support library

    *

      [dep] libgcc2 (>= 4.1.1-12) [m68k]
          GCC support library

    *

      [dep] libgcc4 (>= 4.1.1-12) [hppa]
          GCC support library

    *

      [dep] libsdl-mixer1.2 (>= 1.2.6)
          mixer library for Simple DirectMedia Layer 1.2

    *

      [dep] libsdl1.2debian (>= 1.2.10-1)
          Simple DirectMedia Layer

    *

      [dep] libstdc++6 (>= 4.1.1-12)
          The GNU Standard C++ Library v3

    *

      [dep] libunwind7 (>= 0.98.5-6) [ia64]
          A library to determine the call-chain of a program - runtime

    *

      [dep] ri-li-data (>= 2.0.0-2)
          data files for Ri-li, a toy train simulation game

Download ri-li
Download for all available architectures Architecture	Files	Package Size	Installed Size
alpha 	[list of files] 	43.5 	180
amd64 	[list of files] 	38.4 	156
arm 	[list of files] 	35.8 	148
hppa 	[list of files] 	44.3 	164
i386 	[list of files] 	37 	156
ia64 	[list of files] 	57.5 	236
kfreebsd-i386 (unofficial port) 	[list of files] 	36.9 	110
m68k 	[list of files] 	35.3 	108
mips 	[list of files] 	43.5 	184
mipsel 	[list of files] 	43.6 	184
powerpc 	[list of files] 	41.7 	164
s390 	[list of files] 	38 	156
sparc 	[list of files] 	36.5 	152


I need to download all these aswell?
I have the ri-li deb, double clicking gives the following...
Error :  Dependency is not satisfiable : libc6

Libc6 is already installed on my system, according to synaptic???

---

### Post by stoer on 2007-01-05
Ok got it figured, using alien and the guide in French using the rpm.
Thanks for the deb tip but that sort of overwelmed me with the ammount of manual installs necessary.

---

