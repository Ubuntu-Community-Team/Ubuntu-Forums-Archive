---
title: "Keeping My Settings"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-24
I'm just curious about this....   In windows I have made myself a C: partition that just
host my OS and a D: partition that hosts all my Programs and Personal Files. Now
from my understanding if I reinstalled the Windows OS some of my programs would
work and may or may not hold my settings and some wouldn't work at all.  I am assuming
this is due to the Registry. Not sure if that's true or not I haven't tried it.

So, I'm thinking that Ubuntu ( Linux ) is different in this respect. If I create a 
Home Partition, it will hold all my personal settings even if I reinstall the OS.
Granted, I will have to reinstall the programs but my Settings will hold.
This is all possible because Linux doesn't use a Registry.

Is this true on both points are have I been misinformed?

Thanks

---

### Post by rameshg87 on 2007-10-24
It is true that for most of the programs that run under linux, an individual configuration file is produced in the home directory for each user (if different settings are used for different user). In that case the configurations will be saved, but when you reinstall a particular program after reinstalling the OS, if the installation rewrites the configuration file, then it will be lost. Incase of ubuntu it is good to backup the packages downloaded (from /var/cache/apt)....

---

### Post by dpar on 2007-10-24
Some settings won't work properly. The settings are usually there, you just have to jump through a few hoops the get the program to use them. The majority of the programs will work fine though.:)

---

### Post by dimbulb1024 on 2007-10-24
What amazed me with a fresh install was not having to import Evolution mail on first startup. Same with Tomboy notes. That was pretty cool. :KS

---

### Post by maybeway36 on 2007-10-24
If you have a home partition, the system-wide settings (that are saved in /etc) don't stay, but the user settings (in /home) will. The installation of a program shouldn't overwrite settigns if they already exist.

---

