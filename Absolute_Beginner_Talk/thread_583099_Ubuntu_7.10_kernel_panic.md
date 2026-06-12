---
title: "Ubuntu 7.10 kernel panic"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Taters on 2007-10-20
I have just finished installing 7.10. I was prompted for a reboot, which I did, but the cursed thing gave a me a kernel panic message (mentioned something about apcom or something, I'll post it soon) I am running a live cd right now.

Please help. I'll post the panic message in approx. 5 minutes...


EDIT: ok... I just want to downgrade back to 7.04.... Please help.
Here's the message:

[quote=Linux being mean]MP - BIOS bug: 8254 timer not connected to IO APIC
23.905533 Kernel Panic - not syncing: IO APIC + Timer doesn't work! Boot with apic = debug and send a report. Then try booting with the 'noapic' option.[/quote]


?

---

### Post by Pumalite on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by Taters on 2007-10-20
Okay, here it is:

[quote=Linux being mean]MP - BIOS bug: 8254 timer not connected to IO APIC
23.905533 Kernel Panic - not syncing: IO APIC + Timer doesn't work! Boot with apic = debug and send a report. Then try booting with the 'noapic' option.[/quote]


Help? How would I boot with the APIC/noapic options?

---

### Post by Pumalite on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by Taters on 2007-10-20
I don't get it, is the APIC thing just a resolution error?

---

### Post by deadgobby on 2007-10-20
I am too getting 
24.720279 kernel panic-not syncing: VFS: Ubable to mount root FS on unknown-block(0.0)

---

### Post by taistelutipu on 2007-11-30
jep, that is precisely the message that I also get after having tried to upgrade to gutsy. the kernel panic and unable to mount root on unknown-block. Unfortunately this thread ends here. Has anyone found a solution yet?

I'm currently reading the kernel tutorial. I'll update this post if I think that I've found something for the kernel panic in this case.

*update* I'm through. It helped me to understand a bit better what happens during the booting process but still I don't know what to do about the kernel panic. I googled the error output above and found many different kernel problems but I never found the answer to my central problem: how to I get to the command prompt before the booting process halts with the error message? After that the cursor freezes and I can't type anything anymore. What can I do now?

---

