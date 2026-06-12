---
title: "Can install Xubuntu on Vega86 processor?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by seidleroni on 2008-04-01
Hi everyone,

I wanted to know if it was possible to install Xubuntu on a Vega86 processor (533 MHz).  I know its not Intel/AMD, but is it possible?

[http://www.dmp.com.tw/tech/vega86/](http://www.dmp.com.tw/tech/vega86/)

I would be very grateful for any info!

Thanks,

Seidleroni

---

### Post by angryfirelord on 2008-04-01
According to your article, it's a Via Corefusion, which is essentially an Eden chip with a northbridge attached to it. That's an x86 chip, so the i386 image should run fine. It may not run super fast, but it shouldn't give you any major problems.

---

### Post by seidleroni on 2008-04-01
Thanks AFL,

I will check it out and give it a whirl.  I would think the speed would be OK as its 533 MHz, and 256 MB SDRam.  Do you think it would be uncapable (or poorly capable) of running Mozilla browser with flash heavy websites?

---

### Post by angryfirelord on 2008-04-01
> **seidleroni said:**
> Thanks AFL,

I will check it out and give it a whirl.  I would think the speed would be OK as its 533 MHz, and 256 MB SDRam.  Do you think it would be uncapable (or poorly capable) of running Mozilla browser with flash heavy websites?
256MB will be enough for Xubuntu, but flash has always been wonky. Even on my Core 2 Duo it still acts up on Linux because in my opinion, flash on linux still sucks, no matter what distro you use. Of course, it doesn't hurt to try. I don't have a lower-end system to test with.

---

### Post by c-ron on 2008-04-01
Well, the fact that the website you linked to can't spell Linux correctly isn't promising. 
However, the processor is x86 compatible. Xubuntu should run on it using the -i386 kernel.
You will need to have the xserver-xorg-video-savage package for the S3 ProSavage4.
The soundcard uses the snd-via82xx alsa module.
I'd try installing with the Xubuntu alternate installer. Good luck!

---

### Post by Bölvaður on 2008-04-01
> **c-ron said:**
> I'd try installing with the Xubuntu alternate installer. Good luck!

Actually, my first choice would not be ubuntu at all.... but a proper lightweight distro like puppy or damn small linux. It would run a little but smoother on his computer. But if it has to be Ubuntu then c-ron is spot on.

---

