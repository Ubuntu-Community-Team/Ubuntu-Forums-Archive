---
title: "update hosed my clamshell!"
date: 2007-03-03
forum: Apple PPC Users
---

### Post by Threeethan on 2007-03-03
Hey everyone. 

So -- I've had a good installation of edgy on a 300mhz iBook clamshell going for awhile now, so good, in fact that I decided to get a new battery and an airport card for use around the house.  Today I decided to updated the thing using the "update manager," which seemed to go just fine.

Until I rebooted.  Suddenly I get a "udevd address already bound" error, and it seems that at least one of my partitions is not mounting.  I also don't get a login, since the machine doesn't make it to x-windows, so it's a bit hard to tell exactly what's going on.

I'm going to dig up my install / recovery cd and see what shakes out, but I was hoping that maybe someone else had this error also.

Oh -- I booted the older (prior to update) kernel, and it's the same, so it seems like it may be boot configuration as opposed to kernel.

Thanks!

---

### Post by Threeethan on 2007-03-03
OK -- I didn't do a darn thing, but it's started working again.  It looks to me like it was unable to mount my partitions correctly because of a problem with udev -- which disappeared???

All I did was load up the install cd to mount my partitions and look around.  After I did that, I tried booting again, just to get the correct error messages and, lo and behold, it boots just fine.

No idea.  Ghosts maybe, maybe a thermal issue ?  Anyway thanks for reading, I'm going to go burn some incense and wave it around all my electronic devices now, to appease their spirits.

-Ethan

---

### Post by Clordio on 2007-03-03
Lol, glad to hear it. I'll be sure to keep my install cd on hand just in case.

---

### Post by grazie on 2007-03-03
Although it works sometimes, Update Manager has reputation of being buggy and hence causing lots of problems. I think in this particular case it was just that the udev config files needed to sort themselves out.

---

