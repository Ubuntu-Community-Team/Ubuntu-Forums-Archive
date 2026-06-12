---
title: "ubuntu 7.10 install problem"
date: 2007-11-12
forum: Apple PPC Users
---

### Post by sunnyhanda on 2007-11-12
Hi guys 
ii have imac g3 (1gig RAM, 20 GIG hard drive) and using ubuntu 7.04 feisty fawn which works perfect, today i try to fresh install for 7.10 ubuntu like as i did for previous version but did not succeed.

1 i put cd in drive 
2 hold c key so that it can boot from cd
3 booting option comes - so i press enter 
4 In this section white screen comes with few lines written on the screen 
5 later black screen comes with "loading kernel" 
6 after this suddenly imac turn off (gives a sound as it did after shutdown) but power button still glowing green light.

later i tried to look around so i found this thread so i did as it say"live-nosplash single" but it gives another command line prompt. i dont know what it is but it says as follow

busy box V1.1.3 Debian 1.1.3. 5 ubuntu 7 bash
(initramfs)
Buitin command:   
                                       many linux commands(as i can assume) 
what should i do now, how to start installation.
 
[http://ubuntuforums.org/showthread.php?t=579487]("http://ubuntuforums.org/showthread.php?t=579487")
what is the problem

---

### Post by Auria on 2007-11-12
look a bit around there's tons of threads about gutsy problems on PPC, and many look like yours ;) (i haven't tried myself so i can't be more precise)

---

### Post by blaamann on 2007-11-12
Same problem here on a G4 Windtunnel.

---

### Post by stmiller on 2007-11-12
The Gutsy iso has a horrible bug where it does not load the module for IDE hard disks. See this thread for a fix:

[http://ubuntuforums.org/showthread.php?t=581280](http://ubuntuforums.org/showthread.php?t=581280)

---

