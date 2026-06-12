---
title: "I Thought Linux doesn't freeze"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-07-04
Recently I've been experiencing permanent freezes with my computer (does that make it permafrost?). Most of the time, these freezes have occured during fairly lowend (in my opinion) web browsing. I've experienced uninterruptible freezes (ctrl + alt + bkspace did nothing) while using FireFox and Songbird's browser. I am very worried that I'll be working on something someday and I'll lose it all. How can I find out what's making it freeze, how can I correct it, and how do I automatically send bug reports like I read I could do somewhere while installing ubuntu so that devs can get my info?

Adam L.

---

### Post by coldstatue on 2007-07-04
fwiw - I often have problems like this with video sites like youtube. If I can, I bring up a terminal and enter pkill firefox. Half of the time I get a total lock, and ctrl+alt+backspace does nothing and I have to unplug. For me, it's only video sites.

---

### Post by PhatStreet on 2007-07-04
try adding "noapic" to the end of the boot parameters in GRUB

---

### Post by Wiebelhaus on 2007-07-04
Run full diagnostics on PSU,RAM,HDD,MB,GPU use manufacturers hardware diagnostics all of which can be downloaded from their sites , you gain this information from tools like everest,cpuz,SIS or just open the case and look.

---

### Post by arya6000 on 2007-07-04
I think Macromedia Flash is the reason for this, You can add a force quit button to your tool bar, thats what I did, and its very useful. You press the button than click on application thats not responding and it will end it.

---

### Post by fattom23 on 2007-07-04
I used to have problems very similar to yours when I was running Feisty.  I solved the problem by installing Dapper instead.  I've generally found it to be much more stable, particularly when running web browsers (all of which seemed to cause problems for me).  Hope it helps!

---

### Post by alienexplorers on 2007-07-04
Firefox running flash & Java programs is known to lock up due to high CPU usage.  This is especially true if you have a lot of tabs open.

---

### Post by kerry_s on 2007-07-04
> **Protagonistics said:**
> Recently I've been experiencing permanent freezes with my computer (does that make it permafrost?). Most of the time, these freezes have occured during fairly lowend (in my opinion) web browsing. I've experienced uninterruptible freezes (ctrl + alt + bkspace did nothing) while using FireFox and Songbird's browser. I am very worried that I'll be working on something someday and I'll lose it all. How can I find out what's making it freeze, how can I correct it, and how do I automatically send bug reports like I read I could do somewhere while installing ubuntu so that devs can get my info?

Adam L.

what are your specs?
are they flash sites?
have heavy java?
do you have lots of extentions?

---

### Post by mjwhitfield on 2007-07-04
would using crtl alt +f1 and logging in again, then using pkill to stop firefox not fix this?

---

### Post by coldstatue on 2007-07-06
> **fattom23 said:**
> I used to have problems very similar to yours when I was running Feisty.  I solved the problem by installing Dapper instead.  I've generally found it to be much more stable, particularly when running web browsers (all of which seemed to cause problems for me).  Hope it helps!

My problems with this started after Feisty upgrade.

but yes, multiple tabs makes it worse, I think... but it happens even with just one on You Tube.

---

### Post by zero244 on 2007-07-06
I dont have problems with Flash stuff, but I know Firefox can lock your machine under the right conditions. 
Are you running Beryl or another Composite manager.
It sounds like a video card.......or video driver issue to me. Or something video related.

---

### Post by Protagonistics on 2007-07-08
I do not use Beryl or any like-minded program. I have a dell laptop 3 yrs old, 5150, 30 gig, 512 ram, 64 mb vid card. When using windows, I never had any problems except when playing videogames as it would be horrendously slow even while my friend with the exact same laptop played them fine. Dell never would believe me that my car was screwy- last time I buy from them. 
Anyway, My cd burning is usually at quite low speeds, I rarely have more than 3 tabs open in firefox, I never watch more than 1 video at a time in firefox. I plugged my printer in yesterday and it froze. very odd. I understand this is common among feisty users and It is certainly becoming more common on my machine (3 times yesterday).
I decided to reinstall with Dapper since it is supposed to be more stable. No Problems yet.

---

