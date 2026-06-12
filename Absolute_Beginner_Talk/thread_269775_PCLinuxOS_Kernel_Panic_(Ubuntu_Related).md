---
title: "PCLinuxOS Kernel Panic (Ubuntu Related)"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by trashbird1240 on 2006-10-02
Hello Ubuntu Forum,

After reading that many on this forum have had similar problems connecting to the internet after an Ubuntu 6.06 install, I decided to install PCLinuxOS, which has always worked on the LiveCD -- try it out and see if I have the same problem.

Now I have a different problem.

When I booted PCLinuxOS -- after a full install, and installing the bootloader to the MBR, I received the following message:

kernel panic, no init found (try passing init= at boot)

This sounds like a bootloader problem to me, a newbie.

Could the Ubuntu bootloader be hanging around on my MBR and causing this problem?

I reinstalled PCLinuxOS twice and still got the same message.

If this is Ubuntu related, please let me know and where I can go to find the solution.

Thanks,
Joel

---

### Post by haxer on 2006-10-02
hmm isnt it so that ubuntu uses grub and pc linux uses LILO? :-k

---

### Post by trashbird1240 on 2006-10-02
> **haxer said:**
> hmm isnt it so that ubuntu uses grub and pc linux uses LILO? :-k

Ah...yes PCLinuxOS uses LILO.  How can I get rid of grub so that I can properly install something else?

Joel

---

### Post by tseliot on 2006-10-02
I guess you should try asking on their forums since other users might have had the same problem

---

