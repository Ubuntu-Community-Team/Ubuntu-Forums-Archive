---
title: "dual boot,Ubuntu keeps time, XP looses time resets to 12:00"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-04-06
I'm dual booting XP Pro 64 and Ubuntu 32.  Ubuntu is the default and XP is the second choice.  When I boot into XP the clock is wacked out.  Usually reset to 12:00.  Last time in it also reset the monitor to minimum resolution. Is there a fix for this.  I read some of the threads suggested when I started this post.  Got awful confused.  Where did the changes they were making go, XP? Ubuntu?  Just want XP to keep its proper time and settings while not in use.

Mark Shuman

---

### Post by skymera on 2008-04-06
How did you install Ubuntu?

Wubi? or the mans way, by peratitioning?

---

### Post by northern lights on 2008-04-06
> **skymera said:**
> Wubi? or the mans way, by peratitioning?
As if "Wubi" didn't involve partitioning...
Nuff said.

Back to topic: Have you checked what time is set in your BIOS? Are either OS' synchronous with that?

---

### Post by ghost_ryder35 on 2008-04-06
enable netsync on the clock panel to keep it in sync with some internet time servers.  Seems weird that XP is forgeting and Ubuntu is not, possible BIOS clock battery is dieing or is not set right... Try resetting your BIOS to default and see if that helps.

---

### Post by phread59 on 2008-04-06
I used a live CD.  I unhooked the SATA drive that Windows is residing in.  I hooked up an PATA drive I had laying around for another project.  I ran a straight install on the PATA drive.  Hooked the Windows drive back up and then used Bulldog's setup listed here in one of the dual boot threads.  I modified Grub to add Windows and mapped my drives.

I have no problems whatsoever with Grub.  I can choose and load either just fine.  I just have Windows forgetting the clock settings.

I believe my BIOS is set to default.  I will go and recheck.  While there I will check the clock if I am able to do so.

Mark Shuman

---

