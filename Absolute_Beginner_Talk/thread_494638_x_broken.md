---
title: "x broken?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by bella96793 on 2007-07-07
just installed ubuntu studio version all went ok but it did seem to hang for a while at bitty? then I boot up and it says that x server? is broken . . . I'm very green with any and all commands, it wants me to fix it but don't know what to input. :( 

I can still use vista tho  . . . any advice, please help . . .

---

### Post by RomeReactor on 2007-07-07
Hi. What version of Ubuntu are you running? Also, what video card do you have?

---

### Post by bella96793 on 2007-07-07
don't know what video card I have, so I panicked and instead of trying to fix it (ubuntu studio), I installed regular ubuntu over it and it seems to be working so far . , , :)

---

### Post by flat4 on 2007-07-07
I had a the similar problem, I had regular Ubuntu 7.04, then found Ubuntu Studio, so i fubar my current install and loaded Ubuntu Studio. I also get the X server error and cannot get the desktop.


I have an acer travel mate 4670 with Mobile Intel 945 Express chip set, any help would be appreciated. Or I will have to go back to regular feisty fawn and just add the repositories but that is not cool.


PS. Why is there like 5 different versions that you can boot into? none of them work for me.

---

### Post by bella96793 on 2007-07-07
same here normal ubuntu is fine but studio looks for a video card and I've no idea what I have , my lapop is a HP DV6263CL

---

### Post by shaft350x on 2007-07-15
Same problem here, HP pavilion zv6000 with ATI radeon xpress 200M.

---

### Post by flat4 on 2007-07-16
I found a great how-to here, you need really find out what chipset you have.

the trick for me was to use the Intel i810 driver when I ran the reconfigure package.

Then I booted into x and immediately downloaded the auto script for the i915 drive for Intel that did the job.


As or the ATI do a Google search for your video card model and x server you might get something.

---

