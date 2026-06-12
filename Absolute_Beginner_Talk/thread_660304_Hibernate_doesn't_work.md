---
title: "Hibernate doesn't work?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2008-01-06
After installing Ubuntu 7.10 I can't get Hibernate to work. The screen just turns black with a curser blinking in the upper left corner.

Hibernate worked fine in Ubuntu 7.04.

Don't know where to look to fix this problem - advice would be greatly appreciated!

:confused:

---

### Post by ryanVickers on 2008-01-06
how long does this last?  Mine does that too for a bit and then says a bunch of stuff to do with USB and then powers down OK - restores fine as well...

is your available swap -ge used RAM?

---

### Post by pointyblue on 2008-01-07
It continues until I turn off the power. 

Sorry, I don't understand this sentence:

> is your available swap -ge used RAM?

Thanks for trying to help out, btw. 

:cool:

---

### Post by ryanVickers on 2008-01-07
haha sorry bit of programming babble ;)

hibernate puts all your used ram into swap, but if there isn't enough free, it won't work. ex. if you used 700Mb or ram, but only had 512mb free swap, it wouldn't work

---

### Post by pointyblue on 2008-01-07
Hmm... How do I check that?

My machine has 512 mb.

---

### Post by LowSky on 2008-01-07
gparted would tell you , also in terminal type fdisk -l  (thats a lower case L)

---

### Post by ryanVickers on 2008-01-07
go into System > Administration > System Monitor and in the Resources tab, make sure your "Used Memory" is less than how much swap is available (total - used)

---

### Post by pointyblue on 2008-01-09
Hibernate is working again!

I disabled the restricted graphis driver (didn't use it in Ubuntu 7.04), rebooted and voila - hibernate works like a charm! 

I'd like to know what causes this problem and if it can be fixed, though. Too bad to have to choose between the better restricted graphics driver or the hibernate function...  ](*,)

---

