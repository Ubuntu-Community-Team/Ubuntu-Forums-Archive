---
title: "Feisty shutdown"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-05-10
shutdown shuts the system down but not completely. It did shutdown completely prior to installation using the live cd. After installation it appears to shutdown. Orange bar deminishes then just sits there with a Ubuntu screen.

Tried shutdown -h now and it does the same.

Since another thread has been talking about hibernate and suspend i wondered what my problem is about?

---

### Post by blueturtl on 2007-05-10
I fixed a similar problem by updating the BIOS to the latest version.

If that scares you, you could just try inserting acpi=force to the kernel boot parameters in the /boot/grub/menu.lst file or directly in Grub when the system boots.

Are you sure the system is capable of shutting down on it's own? If the same thing has worked before (say in Windows) then it's likely that the problem is with Ubuntu playing it safe and not enabling automatic power management (APM)...

---

### Post by darkworld on 2007-05-10
Thanks a lot for the reply. I did a bit of research but most shutdown problems were not like mine.

It worked ok in dapper and it worked ok with feisty Kubuntu, has only been a problem since I switched to feisty ubuntu. I noticed that restart takes it right down.

I will try the acpi=force in grub.

---

### Post by darkworld on 2007-05-10
That sorted it! Many thanks.:)

---

