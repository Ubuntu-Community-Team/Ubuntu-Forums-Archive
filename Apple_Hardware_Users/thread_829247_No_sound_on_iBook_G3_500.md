---
title: "No sound on iBook G3 500"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by anubis2591 on 2008-06-14
Hi, I installed Xubuntu 8.04 on my iBook G3 500 and I fixed the display problems by editing my xorg.conf but I couldn't find anything for getting the sound to work. Besides that everything else works fine (even though it's confusing not being able to ctrl-click in some applications). I'd appreciate any help you can give.

---

### Post by stream303 on 2008-06-14
Looks like that sound module problem is still around for some machines (thanks mchladek!).  Have you tried adding

snd-powermac
to
/etc/modules

I'd also be sure to use alsamixer in a terminal and see if anything is muted etc...

---

### Post by anubis2591 on 2008-06-14
Yep, that worked. Thanks.

---

### Post by Monk22 on 2009-04-19
i have this in my ect/modules file already but the sound still doesnt want to work?  i have control over the volume and it doesnt look like its muted in alsamixer from the terminal.  to clarify it doesnt look muted but there is a no symbol over the speaker on the corner display.  any other ideas?

---

