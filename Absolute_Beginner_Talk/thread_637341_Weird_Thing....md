---
title: "Weird Thing..."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-12-10
I have Ubuntu installed on my external Hard Drive.

So I turned on as normal and the Ubuntu loading showed, then after the loading screen it went black and basically said

Starting Drive
Starting kernal
Starting Clock

Something along those lines, then is said this

"/dev/sdc1   Has been mounted 32 times without being checked, check forced."

So after it went through the % check it loaded normally and everything is fine.


What does this all mean?

Thanks for the help.

---

### Post by -grubby on 2007-12-10
the filesystem EXT3 forces you to "check"(similar to chkdsk in windows) your hard drive every  30 or so reboots...nothing to worry about...it's completely normal though sometimes a bit annoying

---

### Post by overdrank on 2007-12-10
> **GeorgiaBoot said:**
> I have Ubuntu installed on my external Hard Drive.

So I turned on as normal and the Ubuntu loading showed, then after the loading screen it went black and basically said

Starting Drive
Starting kernal
Starting Clock

Something along those lines, then is said this

"/dev/sdc1   Has been mounted 32 times without being checked, check forced."

So after it went through the % check it loaded normally and everything is fine.


What does this all mean?

Thanks for the help.

Hi and the only way I can explain it is that is is a maintenance that is done every so many boots. It is all good. :KS

---

### Post by louieb on 2007-12-10
Absolutely normal. Ubuntu is set up to do a file system check every so many restarts. The file system check interval can be adjusted - or - turned off. I just let the file system check  run when it come up.

---

### Post by GeorgiaBoot on 2007-12-10
Okay great, I thought since it did nothing to the system it had to be some sort of planned thing. But always nice to have peace of mind.

Thanks for the help.

---

