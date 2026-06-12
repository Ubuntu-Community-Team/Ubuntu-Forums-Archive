---
title: "[SOLVED] Gutsy Raising Skinny Elephants fsck stall"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by SpiritIsReality on 2007-11-08
howdy
7.10 Desktop Edition fsck check after about 30 starts, stalls.
I held down the Alt and PrintScreen/SysRq keys while I typed each of the next
word's beginning letters, about 2 or 3 seconds between each one.
Raising Skinny Elephants Is Utterly Boring
The computer restarted  successfully. Your mileage may vary.
[http://ubuntuforums.org/archive/index.php/t-23708.html](http://ubuntuforums.org/archive/index.php/t-23708.html)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%28gutsy+OR+7.10%29+fsck+stall&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%28gutsy+OR+7.10%29+fsck+stall&btnG=Google+Search&meta=)

---

### Post by philinux on 2007-11-08
Ok so when it stalls whats the error message if any.

---

### Post by SpiritIsReality on 2007-11-08
howdy
Phil ! Ya I guess I'd better mark this thread solved. Thanks.
When the fsck said it was checking the filesystem,it stalled there and just below the fsck there
was a pulsating - (dash)
trails

---

### Post by Herman on 2007-11-09
>  When the fsck said it was checking the filesystem,it stalled there and just below the fsck there was a pulsating - (dash)Just be careful if you have any file systems in the machine that are anything other than ext2 or ext3.
It might not really be stalled, it might just be busy for a while.
The ext type file systems support a progress bar, (like a tumbling bar followed by a row of = signs to show you that something is happening.
When fsck is working on other file systems like reiserfs or something else, there will be no progress bar, you just have to know you have to wait a few minutes and be patient.
Link:  [Automatic filesystem checks on bootup]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_checks_on_bootup")

Thanks for that interesting link about the keyboard shortcuts, I like that, I need to study it and then I think I'll bookmark that one! :)
And you are right about using 'Raising Skinney Elephants Is Totally Boring' to shut down a Linux system that is frozen, I do that too if I ever need to.

Regards, Herman :)

---

### Post by SpiritIsReality on 2007-11-09
howdy
Herman
>  Just be carefulthanks
trails

---

