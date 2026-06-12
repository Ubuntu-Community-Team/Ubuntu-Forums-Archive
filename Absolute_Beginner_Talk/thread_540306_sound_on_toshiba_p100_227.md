---
title: "sound on toshiba p100 227"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by ovidiul on 2007-09-01
hi.
can anyone help me - it seems possible, but how to do it? if someone could tell me step by step, what to do , it would be greet.
thank you.
ovidiu

---

### Post by Daveth on 2007-09-01
do you mean you have no sound at all- no drums to log-in, or just no sound with cds, movies etc. In otherwise is the tosh completely silent?

---

### Post by ovidiul on 2007-09-01
> **Daveth said:**
> do you mean you have no sound at all- no drums to log-in, or just no sound with cds, movies etc. In otherwise is the tosh completely silent?

yes sir, none at all. i tried playin with the settings , between alsa and conexant waikiki mixers, tried all the possibilities, and nothing. i do not know how to insall other drivers for sound, it is so complicated, please help.
and i thought i know computers... aaaaaaaaaaaa!!!!!

---

### Post by Daveth on 2007-09-03
um, not looking to good at the minute....

[http://www.linlap.com/wiki/Toshiba+Satellite+P100](http://www.linlap.com/wiki/Toshiba+Satellite+P100)

which alludes to ALSA not covering this laptop at the moment. Not sure where this leaves you save for keeping an eye on the ALSA pages to see when the reported bug is squashed. This at

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Anyone else any ideas?

---

### Post by maxfacta on 2007-09-04
Sound *can* be made to work on this hardware! I have just finished the adjustments.
Rebooted and then nearly fell off my chair when Ubuntu welcomed me with some chimey noises, a new sound for me :)


I basically followed the steps outlined here:
[http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html](http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html)

A few points regarding using these instructions with Ubuntu:

The iasl packaged by ubuntu will do the job fine, so no need to download and compile the source.
IE, replace steps 1 - 4 with an 
#aptitude install iasl
or whatever package management tool floats your dinghy.


He mentions a "fixed DSDT file". I don't  think it's cool to simply download and use it. It was different from the DSDT.dsl file my system generated.

In step 6, I wouldn't recommend *replacing* a grub entry with your new boot configuration, but rather adding a new block. At least until you're sure it boots and works for you.


Good luck. My success is the culmination of many hours spent poking at this problem, trying various fixes that Google pointed me at. Hopefully this will work for you too.


- Thought I'd post this little perl 1-liner I used, when replacing the _T_n with TXTn.
# perl -pi -e 's/_T_(\d)/TXT$1/' DSDT.dsl

---

### Post by proud2bcdn on 2007-09-04
Thanks maxfacta...I'm going to try this out in the next few days cuz I'm really wanting to dump MS from this notebook!!

---

### Post by maxfacta on 2008-01-05
Well, after upgrading to Gutsy it was disappointing to see that the sound was not supported out of the box. And more disappointing to find that the above fix no longer provides any audio :(

[And then even more disappointing to find a new problem - the system can't drive the cooling fans. Now the laptop gets hot and shuts itself off with any kind of intensive activity]

---

