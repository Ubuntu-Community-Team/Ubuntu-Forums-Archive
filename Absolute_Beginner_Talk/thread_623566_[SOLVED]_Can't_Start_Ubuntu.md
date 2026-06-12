---
title: "[SOLVED] Can't Start Ubuntu"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by wiseguy1515 on 2007-11-26
Hello,
I just got back from Thanksgiving vacation, and on the plane I watched a movie in Ubuntu Gutsy Gibbon. When I got home and turned on my laptop and tried to boot into Ubuntu, it displayed the following:

"RAM DISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)"

It showed this before even starting to load Ubuntu. 
Moreover, I have Windows XP installed as well, and that boots up just fine.
Any ideas?

Thanks!

---

### Post by wiseguy1515 on 2007-11-26
Oh and I forgot to add, when I shut down the laptop after watching the movie it got stuck and wouldn't shut down for about five minutes, so I shut it down by holding the power button.

Edit:
Sorry, I keep thinking of new things: I tried booting in recovery mode and it displayed the same thing.

---

### Post by wiseguy1515 on 2007-11-26
bump

---

### Post by dgrafix on 2007-11-26
No idea, not seen this before. HDD corruption/faliure mabe?

Try running some disk diagnostics using the live cd :/

---

### Post by deadgobby on 2007-11-26
I been searching and searching for an answer for this. I do not know why your system would do this after a nice clean install. Any ways it is a message of could be doom and reinstall it again sam. 
So try these links and see if you can restore your boot loader.
[http://ubuntuforums.org/archive/index.php/t-27709.html](http://ubuntuforums.org/archive/index.php/t-27709.html)
[http://www.linuxquestions.org/questions/slackware-14/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-361735/](http://www.linuxquestions.org/questions/slackware-14/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-361735/)
I am still researching on this. 
Gobby

---

### Post by ukripper on 2007-11-26
Boot from live cd and do filesystem check using following command:

if on hda:
```
sudo fsck /dev/hda
```

OR

if on sda:
```
sudo fsck /dev/sda
```

Most likely filesystem needs repairing. fsck will do it for you.

MAKE SURE YOU BOOT FROM LIVE CD!!!!

---

### Post by wiseguy1515 on 2007-11-26
Thank you all so much for working on this. I actually got it fixed by using the lengthy procedure outlined here by athomson:
[http://ubuntuforums.org/showthread.php?t=620860]("http://ubuntuforums.org/showthread.php?t=620860")

Thank you everyone and thank you athomson!

---

### Post by deadgobby on 2007-11-28
Cool!!!! I am going to try that out!

---

