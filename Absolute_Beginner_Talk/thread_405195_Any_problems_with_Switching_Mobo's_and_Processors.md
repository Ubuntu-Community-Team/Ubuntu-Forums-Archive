---
title: "Any problems with Switching Mobo's and Processors?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Fenrirwulf on 2007-04-09
Hi! I'm about to switch from a Athlon 64 3400+ and socket 754 Motherboard to a new Socket 775 Intel mobo and Duo Core 2 processor and wondered if Ubuntu would have any problems finding the new hardware or will I have to probably re-install Ubuntu? Right now I have nothing really installed so a fresh install won't kill me, but was just curious if anyone had success doing this before? :-?

---

### Post by jhenager on 2007-04-09
I'd be really surprised if you didn't get a HAL error at least. I have done similar things with Win98, but it wasn't as hardware dependent as this OS.
Especially since you are going from one socket type to another, and AMD to Intel.
I'd do this:
Back up any critical data on removable media.
Try it.
If it works, look at it as a gift, but don't expect it to happen.
Have your Ubuntu reinstallation media ready. Post your results if you would.

---

### Post by Fenrirwulf on 2007-04-09
Yeah, that's pretty much what I expected too. I know sometimes on Windohs you can pre-install some of the motherboard drivers before you do a switch and it will detect it after booting up, but wasn't really sure about Ubuntu or not. I'll keep ya posted. :)

---

### Post by qamelian on 2007-04-09
> **Fenrirwulf said:**
> Yeah, that's pretty much what I expected too. I know sometimes on Windohs you can pre-install some of the motherboard drivers before you do a switch and it will detect it after booting up, but wasn't really sure about Ubuntu or not. I'll keep ya posted. :)

Try it...you might be surprised. I've replaced the mobo on my desktop 3 times with needing to re-install. The only time I've ever had a real issue was replacing a video card with one from a different vendor and even that only required reconfiguring x.org.

---

### Post by Fenrirwulf on 2007-04-09
Sweet! I can't wait to try it out. Mobo's on the way from Newegg and I get to pick up the processor this weekend.

---

### Post by John Williams on 2007-04-17
I went from a K6-2 on a PCChips MB (5+ years old, SIS onboard video) to a ECS 945G-M3 (i810 video) and an Intel Dual core EM64T. Booted right up and all I had to do was reconfigure xserver for the new video. Also, during the install, used gparted to move the partitions from a IDE to a SATA drive. Used SuperGrub to rebuild the MBR. I was amazed and actually quite surprised. 

This was on the Feisty Beta....

---

