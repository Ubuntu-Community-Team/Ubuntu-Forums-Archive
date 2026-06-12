---
title: "need help"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by disco2000 on 2007-04-29
I have just burned my Ubuntu 7.04 Live CD and tried to load it onto my Dell Inspiron 6400 laptop only to get this message:

> 
"[116.592000]  bcom43xx: Error : microcode 'bcm43xx_microcode 5.fw" not available or load  failed.  further along it tells me :

(EE) VESA (0): no matching modes.
(EE) Screens found but none have usable configuration.



What can I do? Can anyone help a first timer with Linux?

disco2000

---

### Post by apunc1 on 2007-04-29
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

It deals with Feisty Herd 5 but it has the same error message.

---

### Post by disco2000 on 2007-04-29
Thanks for the reply. I have read the whole bug #89853 report and discussion, but being a total newbie to Ubuntu or Linux for that matter, I do not see a solution for my problem. 

It seems the bug has to do Dell Inspiron 6400 Core Duo with an an ATI Mobility Radeon x1400 card trying to install Feisty i386. Native resolution is 1440x900. 

Should I wait until they fix the bug and burn another DVD when it is fixed??

Disco2000

---

### Post by apunc1 on 2007-04-29
have you tried to edgy? it seems the people have your problem can run edgy.

i would think it will be fixed in feisty in an upcoming update, but if you can get edgy running you can update to feisty after the problem is fixed.

---

### Post by jerrylamos on 2007-04-29
I have a completely different computer, IBM NetVista, which had the "screens found...." error.  In this case, from a posting (6 months ago), I went into Bios and looked at the shared screen video memory (I don't have that computer up to see the exact words).  It was set at 1024 kb.  I changed it to 8096 kb which allowed boot up.  It's an Intel 82845G graphics chip which actually uses 65536 kb of shared memory to run, but apparently the 8096 kb was whatever boot needed to come up.

XP didn't have a problem; since it "came with" it worked.  Another older computer the highest I could set the bios to was 4096 kb which was enough.

Cheers, Jerry

---

### Post by apunc1 on 2007-04-29
don't know if you've seen this or not [http://ubuntuforums.org/showthread.php?p=2562327#post2562327](http://ubuntuforums.org/showthread.php?p=2562327#post2562327)

using the alternate cd instead of the regular live cd and installing in text mode might solve your problem

---

