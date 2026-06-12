---
title: "Having difficulty with sound?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by tmskraus on 2008-04-01
I've been trying to fix my sound for hours. First, I noticed that both my speakers and my headphone were playing at the same time. I was able to fix that (after *a lot* of Googling). About 10 minutes later, I lost all sound. A few hours later, I was able to fix that, too. I restarted the computer and I had sound back, except I now had sound in my headphones and speakers. I fixed that, using the same method as I did before. Some time later, I lost all sound (this is my current state). :( 

What's going on? I really need help. :confused: This is probably the last thing I need to do before I can use Ubuntu normally (today I've fixed my wireless connection, flash, my screen resolution, and some glitch with Compiz). :lolflag:

Thanks.

---

### Post by tmskraus on 2008-04-01
Any ideas?

---

### Post by tmskraus on 2008-04-01
Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

---

### Post by spiderbatdad on 2008-04-02
see if this applies to you: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

if not, try```
asoundconf list
asoundconf set-default-card Parameter
```where Parameter is the result of the first command.

BTW I assumed you had Gutsy?  Maybe upgrade to Hardy beta...using pulse audio has fixed sound issue for some.

---

### Post by tmskraus on 2008-04-02
I've tried the thing for my laptop but it comes up with an error after some steps. 

I set Nvidia as the default card.

---

### Post by _aXXe_ on 2008-04-02
> **tmskraus said:**
> I've tried the thing for my laptop but it comes up with an error after some steps. 

I set Nvidia as the default card.

Is your unit a laptop with an intel chip and an intel sound card? if so check this out.



[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)


I used it on my desktop with an intel chip. It works in Skype.

---

### Post by cherry316316 on 2008-04-02
any success any one so far ?

---

### Post by spiderbatdad on 2008-04-02
We should know what distribution folks are seeking support for. Please post your ```
uname -r
``` so we  know what kernel you're running.

It is possible software sources are not enable,  or restricted modules are not installed/selected.

---

### Post by tmskraus on 2008-04-02
> Is your unit a laptop with an intel chip and an intel sound card? if so check this out.



[http://www.antonywilliams.com/2007/1...ling-alsa.html](http://www.antonywilliams.com/2007/1...ling-alsa.html)


I used it on my desktop with an intel chip. It works in Skype.

No, it says my sound card is nVidia? I'm not sure. 

spiderbatdad: 

> 2.6.22-14-generic

---

