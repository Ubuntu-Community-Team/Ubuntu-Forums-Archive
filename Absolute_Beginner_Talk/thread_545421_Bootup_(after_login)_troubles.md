---
title: "Bootup (after login) troubles"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-09-07
something's wrong with ubuntu on my laptop. I'd like to be more specific but I don't know what it is.. the login takes too long (starting of ubuntu after I submitted my name/pass...) 

what logs should I check?

it might be graphics related. It started when I was playing game - Battle Tanks and it froze (I had compiz running) so I tried restarting X, it restarted but it was VERY laggy.. next time I booted there was this problem with boot taking too long...

edit: I forgot to mention my laptop is HP nx7400 with intel 950 gpu...

---

### Post by jnorthr on 2007-09-07
dmesg
from a terminal command line just aftr you boot up might just give us some clues as to what the kernel is doing with each component of your hardware.

---

### Post by kane77 on 2007-09-08
okay.. other symptoms - programs take unusualy long to start (2-5 minutes for terminal...) and computer doesn't seem  busy at all..

also desktop-effects cannot start and they worked before... I include some logs (dmesg output, kern.log, syslog) they were taken right after the system booted...

---

### Post by jnorthr on 2007-09-08
Great ! Thanx for that. I'll have a look at them tonite.

Just an idea - what is the size of your swap file partition ? Is there any chance this may have changed ? If too much work is going on and ram is not sufficient, the swap partition is used. Is it twice the size of your system ram ?

What desktop effects do you have running ?

---

### Post by kane77 on 2007-09-08
> **jnorthr said:**
> Great ! Thanx for that. I'll have a look at them tonite.

Just an idea - what is the size of your swap file partition ? Is there any chance this may have changed ? If too much work is going on and ram is not sufficient, the swap partition is used. Is it twice the size of your system ram ?

What desktop effects do you have running ?

I had compiz running, but now it cannot start (at one time I could not switch it off, in System -> Preferences -> Desktop effects I turned it off, but it just stayed on so I restarted the system and now it won't come on...)

my swap is ~1.4 GB and I have 1 gig RAM... I believe it is not the swap because in the period between I click on the icon and the time the program starts there is only minimal hdd activity.. 

thanx for your patience...

---

### Post by kane77 on 2007-09-11
bump

---

