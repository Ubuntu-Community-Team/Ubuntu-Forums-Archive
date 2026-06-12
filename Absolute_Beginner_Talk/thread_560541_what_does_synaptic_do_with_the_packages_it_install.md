---
title: "what does synaptic do with the packages it installs - how do i run them?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by mactece on 2007-09-26
i have an external hard drive which i share with my windows xp laptop. Most times I move between the two systems and boot into ubuntu it refuses to mount the hdd unless it is in ro mode. I can either live with it or (if I have the laptop home from work) try to get windows to shut it down properly.

To solve this I installed ntfsfix with synaptic but now have 2 problems:

1) unlke packegae manager, synaptic doesn't sem to install the programs with a nice link to click on- so where is the program and how do I get to it.

2) how do I get ntfsfix to work with a disk which isn't mounted because it needs to be fixed? Is it a catch-22?

---

### Post by darc on 2007-09-26
ntfsfix is a command line utility.  If you open a terminal you can type 'ntfsfix -v' to see that is installed, but you'll be running it from the terminal.

You don't have to mount the drive to use ntfsfix, just give it the hardware (dev) location of the disk like : 

$ntfsfix /dev/hda2

-darc

---

