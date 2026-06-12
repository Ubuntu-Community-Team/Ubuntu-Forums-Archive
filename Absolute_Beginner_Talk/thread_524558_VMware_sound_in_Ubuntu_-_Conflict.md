---
title: "VMware sound in Ubuntu - Conflict"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-08-13
Hi there,

I'm running windows in WMware for those one or two annoying apps that won't run on Ubuntu but that I still need. The one program is a Neural Programmer - the whole program is based on sound. But when I have a media player open or playing something in Ubuntu VMware gives me an error? How can I make VMware share/ play simultaneously?


Thanks in advance,

Rudolf Hoehler

---

### Post by Hospadar on 2007-08-13
I really don't know how to solve your problem, but I suspect that the problem originates from the fact that your VM is (probably) using OSS drivers instead of the alsa drivers.  I know with wine this causes programs to not share sound.  It may not be your problem at all, but check out your vm sound options and see if you can change it, or find some more info along these lines.

---

### Post by RudolfMDLT on 2007-08-14
Thanks! I also think so but in VMware I can only select the sound device - not what driver to use. any body else using vmware solved this issue?

---

### Post by arethz on 2007-11-06
I got the same problem. Seems like the /dev/dsp can't support multiple programs running simultaneously. Any Idea?

I'm running  backtrack 2 within gutsy box with vmware.

---

