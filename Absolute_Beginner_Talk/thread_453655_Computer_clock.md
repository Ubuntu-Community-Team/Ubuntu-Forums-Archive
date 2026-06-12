---
title: "Computer clock"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by eks on 2007-05-24
Quick simple question (I supose).

I'm living in Prague, normally GMT+1 but with daylight saving time it's GMT+2. Everytime I go to Windows, the clock is 2 hours less than it should (if it's 20, it will show 18 ). If I leave it that way and go back to Ubuntu it's on the correct time (20 is set to 20). If I change in Windows to the right time, and boot Ubuntu, it's on the right time also. But when I boot Windows it's 2 hours less.
[B]
It's like Ubuntu is always setting the clock to GMT but showing my current time (GMT+2). How do I make Ubuntu leave the computer clock in peace so Windows can also share it? :)[/B]

Or, where do I configure this in Ubuntu?


eks

---

### Post by starcraft.man on 2007-05-24
I think I know what this is, its just that you have UTC left on, which you shouldn't if your dual booting (or in general, I don't really use it).

Just right click on the time, push preferences and un check the "Use UTC box". Thats it I think. Then log into windows again and double check.

I think thats all thats the problem, hope that fixes it, post back either way :).

---

### Post by tkjacobsen on 2007-05-24
Edit /etc/sysconfig/clock file and set the line "UTC=true" to "UTC=false", then reboot.

---

### Post by Bachstelze on 2007-05-24
Actually, you should genrally have it set at UTC, unless you're dual-booting. Windoze is the only OS in the whole universe that expects the hardware clock to be set at local time... Just edit /etc/sysconfig/clock and add a line saying UTC=false.

---

### Post by tkjacobsen on 2007-05-28
> **tkjacobsen said:**
> Edit /etc/sysconfig/clock file and set the line "UTC=true" to "UTC=false", then reboot.

And then i found out that this is not true. It was just an old habit form my time on fedora! The right way to do this on debian derived systems is to set the variable UTC=yes in /etc/default/rcS. 

Sorry for the wrong answer before.

---

