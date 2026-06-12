---
title: "Can you help my friend out"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by playme123 on 2007-07-15
he is having the following problem and need help



The laptop is ****ed!!!!!! It's that darn wireless card. It won't recognise it and it freezes whenever I put the card in. I have spent the evening trying to get a utility to work (ndis wrapper) to add a driver for the card, but it would not work. Then I inserted the card again, the laptop froze, and then I pulled the card out agaon. That seemed to knacker it, and it says that the boot file is corrupted and will now install Windows (i.e. there is no option to install Ubuntu). Trouble is, when it tries to install Windows, it gets so far then a blue screen comes up and it shuts down. It then starts again and does the same thing, in an endless loop. Upshot: cannot start laptop at all, even in safe mode. I'll have to reinstall Windows on it and if that doesn't work I'll have to reformat it and start again.
__:KS

---

### Post by Daveth on 2007-07-15
this
 [http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)
will probably help your friend out, though their server is down at the moment. I'm assuming he got to dual boot XP and Ubuntu? Or did it just die at Windows. From recollection supergrub can repair the master boot record in windows- if he only has windows on the laptop at the moment and has the recovery disk, then "fixmbr" (minus the quote marks) typed into the windows terminal should get him back their again.

---

### Post by forestpixie on 2007-07-15
should be able to repair with the windows disc - instead of install you need to do the repair or recovery option - if you get that far :) - and then do fixmbr once you've got into the win partition.

---

