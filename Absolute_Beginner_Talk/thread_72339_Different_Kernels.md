---
title: "Different Kernels"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by KrakHT on 2005-10-06
I've read about i386, i686, and K7 kernels. Whats the best to use? Is there REALLY a performance increase? Is it noticeable?
I have 2.6.12-9-386 running now. I did the uname thing and it says i686. I am also using an AMD AthlonXP 1800..
From what I've read I can use the i386 (default, one size fits all), the i686, or the K7 (for athlons right?). Is it worth it? Should I use i686 or the K7? And if I did, would it break anything (nvidia video)?

---

### Post by matthewv on 2005-10-06
K7 is optimised for the amd processers. I am using the 686 kernel for my PIII, and I dont think there is any real risk of breaking something. You can always boot your old kernel from grub. I don't know how great the performance increase is though. In your case I would use the K7

---

### Post by Mustard on 2005-10-06
If you installed commercial drivers for nvidia (from nvidia website) I think you would need to reinstall them afterwards..I'm not sure.

---

### Post by qiezi! on 2005-10-06
[quote=Mustard]If you installed commercial drivers for nvidia (from nvidia website) I think you would need to reinstall them afterwards..I'm not sure.[/quote] 
It's *possible* you may not need to, I installed nvidia drivers on my AMD64 dual-core processor with the i386 kernel. They ran with no problems. Afterwards I installed a k7 kernel and have had no problems with the nvidia drivers. 

I had a large boost in performance but that is most likely because the k7 kernel had smp enabled, where as the i386 being stock off the CD didn't. For an AthlonXP, the k7 kernel will probably be better than the i386, but by how much I have no clue. Anyone else??

---

