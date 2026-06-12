---
title: "Is acpi necessary?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by johnraff on 2007-06-23
When I bootup I get a message from Grub that the bios is older than 2000 (1999) and "acpi=force" is needed in the grub config file to enable it. The bios will support acpi I think, but the computer seems to be working OK without it.

Is there anything to be gained from enabling acpi?

---

### Post by 5-HT on 2007-06-23
Is it a laptop? If so, acpi could add some extra functionality but apm should do just fine. If you're not missing anything without acpi (suspend-to-ram&disk, CPU temp monitoring, etc...) leaving apm in place won't do any harm.
If you can force acpi and everything works well, go for it. That warning about the bios is a kernel config option implemented to help avoid acpi issues with older machines. It is not to say that your specific machine doesn't work well with acpi.

---

### Post by johnraff on 2007-06-23
It's a desktop, so I don't really need suspend/hibernate type stuff. Presumably "apm" is working now though I wouldn't really know...
The bios options mention acpi here and there so it's presumably supported. I guess I could add "acpi=force" and see what happens. Will it likely use any more RAM? That's what I'm really short of.

---

### Post by 5-HT on 2007-06-23
> **johnraff said:**
>  Will it likely use any more RAM? That's what I'm really short of. Shouldn't be noticeable. ACPI is fairly modularized, so only required modules will be loaded into the kernel when needed.

---

### Post by johnraff on 2007-06-23
Thanks, I'll give it a go...

---

