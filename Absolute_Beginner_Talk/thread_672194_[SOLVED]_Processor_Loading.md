---
title: "[SOLVED] Processor Loading"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by malty on 2008-01-19
One of the things I find annoying with WINXP is its ability to grind my processor into swarf, the main suspects are all of the moats, drawbridges, ramparts, tank traps etc required to stop the tossers getting in ( typically it takes 4 minutes to start up ) add to this Firefox with the IGoogle homepage, CS3, lightroom, you can see the problem.
My computer is reasonably well specified..
Dell Dimension 5000
2.6 G memory.
160G HD = WINXP
500G HD = 3 partitions....P1 = 160G = Ubuntu
                                            P2 = 150G = All of my files from WINXP and
Ubuntu.
                                            P3 = Backups ( and home for a future Distro)
All of the swap memory is correctly set up.
In Ubuntu I have 6 windows set up for various apps.
I do tend to have at least one app open in each widow, in the net window I have Firefox and EMule always open.
Photoshop 7, Varicad, Amorak and Konqueror all tend to be open.
I know that both Firefox and EMule and PS7 are all processor greedy.
I have done all of the checks on memory usage using all of Ubuntus clocks and dials and everything seems to be OK.
Ubuntu starts reasonably quickly, processor is calm.
After loading up the apps and especially when using Firefox the processor goes into overdrive but in waves.
The strange thing is after shutting down EMule and Firefox this behavior carries on. Only shutting down and restarting cures it.
Any ideas please ?
                                             Malty

---

### Post by sumguy231 on 2008-01-19
Install and run htop. It's an excellent command-line system monitor which might help you figure out what exactly is taking your resources.

By the way, I just had to quit Amarok because it was using a bunch of resources for some reason. It was probably rescanning the collection or something. Keep an eye on it.

---

### Post by malty on 2008-01-20
Thanks for the info.
        You are right about Amarok, its using between 43% to 80% of the processors power !, most of the time. It seems to be in a permanent state of scan, none of its settings seem able to control this, I will carry on checking and post the results.
                                                        Kind regards
                                                                                Malty

---

### Post by malty on 2008-01-21
I have reported the following KDE bug.....

Amarok is constantly rescanning and updating the music database, it will not stop.
Unchecking the boxes in settings / configure Amarok / collection makes no difference, even though, in theory, there is nowhere to scan or update.
The end result of this is a massive use of processor power making Amarok unusable.
I am running Fedora 8 in VMWare and have tried to replicate the problem there, Amarok runs faultlessly here so the problem may be in Ubuntu only ?.
                                               Malty

---

