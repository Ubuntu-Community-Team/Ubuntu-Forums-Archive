---
title: "Live cd laptop problem"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by audio_uphoria on 2007-12-12
Hey everyone. I'm having an issue while trying to boot off the live cd I downloaded and burned. I am able to run it on my desktop just fine but when I try to load it on my laptop my screen turns weird. What will happen when I boot is: the ubuntu welcome screen comes up asking me what I would like to do. I choose start ubuntu and hit enter and then a quick message flashes on the top that says "bios bug #81 found" after that the OS starts initializing and during all the system checks I notice another error that reads "error micro code: bcm43xx_microcode5.fw" After that a black grid comes up on the screen and covers the entire screen while a blue/grey blob glows and gets really bright and then slowly fades until the screen is completely blank. Has anyone had this problem or know how I can fix it? Any help is greatly appreciated and the specs on my laptop are on this link:

[http://reviews.cnet.com/laptops/hp-compaq-presario-f572us/4507-3121_7-32473965.html?tag=sub](http://reviews.cnet.com/laptops/hp-compaq-presario-f572us/4507-3121_7-32473965.html?tag=sub)


Thanks.

P.S. My whole issue is the screen when ubuntu loads up.... There is absolutely nothing on the screen except a black grid and a blob of blue/grey which will glow really bright and then fade into darkness and remains that way so there is nothing but a blank screen and I cannot do anything with my computer except reboot. I wasn't sure what those errors were so I thought it might have something to do with my problem and posted them as zabien had suggested in my previous post. Although searching the web has helped me figure out what the error codes mean I can not find anything that will tell me how I can get ubuntu working on my computer. Any ideas?




-Yes, zabien I've been trying to resolve this issue by researching it on the web for the past 4 hours and havn't come up with any solutions. I realize it would've been more polite to edit my previous post and probably would've saved me some time but I'm new in this forum and just figured out how to pull up my previous posts and how to edit them.

---

### Post by lswest on 2007-12-12
the micro code error is from the firmware trying to run for a broadcom card, it doesnt work in Gutsy (yet).  You can basically ignore it, just means you have no working wireless.  Other than that im not sure what the BIOS bug is about...try googling the error to get more information on it?

---

### Post by zabien1970 on 2007-12-12
It would have been more polite to bump your previous thread on this than starting a new one, did you try the suggestions I offered?

---

### Post by subs on 2007-12-12
> **lswest said:**
> the micro code error is from the firmware trying to run for a broadcom card, it doesnt work in Gutsy (yet).  You can basically ignore it, just means you have no working wireless.  Other than that im not sure what the BIOS bug is about...try googling the error to get more information on it?


Googling does not yield any useful information on the bug

i had a similar problem on my laptop.... however using an older kernel version (2933 -  i think) solves the problem ... it no longer shows up

nothing goes seriously wrong with this error.... so dont recompile ur kernel unless u r really pushed into doing it

---

### Post by zabien1970 on 2007-12-12
No prob. I was just following your old thread waiting to see what happened when this one poped up, hope I didn't come across as an ***

---

### Post by zabien1970 on 2007-12-12
Ok, after some searching it appears that 'error micro code: bcm43xx_microcode5.fw' seems to be a problem with the wireless so that can be resolved later, Unfortunately your big problem appears to be with  'bios bug #81', from what I can tell that's a problem with Pheonix Bios and the AMD CPU's for which there doesn't seem to be a workaround, maybe you could try a different distro of linux and see if that works.

---

### Post by subs on 2007-12-12
> **zabien1970 said:**
> Ok, after some searching it appears that 'error micro code: bcm43xx_microcode5.fw' seems to be a problem with the wireless so that can be resolved later, Unfortunately your big problem appears to be with  'bios bug #81', from what I can tell that's a problem with Pheonix Bios and the AMD CPU's for which there doesn't seem to be a workaround, maybe you could try a different distro of linux and see if that works.



in my old laptop.... i had the problem with distros of fedora, ubuntu nd suse..... it is a problem with the kernel... not the distro

---

### Post by zabien1970 on 2007-12-12
> **subs said:**
> in my old laptop.... i had the problem with distros of fedora, ubuntu nd suse..... it is a problem with the kernel... not the distro

Sorry I wasn't clear on that, that's the point I was trying to make, when I said try a different distro it would have to be based on a different kernel, unfortunately I can't offer a suggestion on one since I'm not that familiar what kernels are where

---

### Post by shadow-of-sin on 2007-12-12
Well if it is a bug in the kernel then you should post the bug here:
[http://bugzilla.kernel.org/]("http://bugzilla.kernel.org/")
(remember to check if it hasn't been posted already)

---

