---
title: "Shrinking hard disk?!"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-04-10
I have a small hard disk on my ancient laptop - df -h tells me the total size is 4.1G... at least, it did. My last df -h just said Size: 3.8G! But all i've done since the last time i checked disk space is install gnokii and scanModem. and that shouldnt make /dev/hda _shrink_! cos thats what i'm talking about, it's the total size that's gone down, not free space! Wtf?!

---

### Post by trent dillman on 2006-04-10
Ouch. Maybe check for bad blocks?

---

### Post by gr0kzer0 on 2006-04-10
Bad blocks? Sounds painful. How do i check for that?

---

### Post by trent dillman on 2006-04-10
sudo apt-get install badblocks
man badblocks

---

### Post by gr0kzer0 on 2006-04-10
Thanks... "E: Couldn't find package badblocks". Not on the installation cd, right? I need to get my modem sorted?

---

### Post by gr0kzer0 on 2006-04-10
Thanx 4 the badblocks pointer, but the 'apt-get' advice threw me 4 a bit cos i'm not online - but i did 'man' and 'whereis' anyway and the progs on my default! So, i did a 'sudo badblocks -v /dev/hda1' (as that's my shrinking partition) and: "Pass completed, 0 bad blocks found". (btw, why are man pages so _difficult_?) So good news, kinda. But why's my goddam hard disk vanishing?! ;)

---

