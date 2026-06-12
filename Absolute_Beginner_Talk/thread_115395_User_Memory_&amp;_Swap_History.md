---
title: "User Memory &amp; Swap History"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2006-01-10
At what point does my allocated swap space start being used? How much swap space can I use before I need to reboot? I recently got XP running through VMware and it has 192 MB memory allocated to it. Is that 192 of the original 512 that I have? Am I even close to how this process works and could someone please enlighten me if I'm not? 

Thank you in advance

---

### Post by az on 2006-01-10
"At what point does my allocated swap space start being used?"

Usually at a point set by your swappieness setting in /proc/vm/somethingorother.  It is actually a simple formula that decides what gets kept in memory, what gets paged, what gets cached and what gets dumped.  Probably when about 80 percent of your memory is used, your swap will start to see some filling?  Hard to say.



"How much swap space can I use before I need to reboot?"

You will not need to reboot because of that.  The kernel will free memory before making your system crash.  


"I recently got XP running through VMware and it has 192 MB memory allocated to it. Is that 192 of the original 512 that I have?"

Yes.

---

### Post by Il_Tuo_Nome on 2006-01-10
The thing is, my swap is being used with only 28% of main mem used.

---

