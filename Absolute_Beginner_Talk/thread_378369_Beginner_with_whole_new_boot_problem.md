---
title: "Beginner with whole new boot problem"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-03-07
when I start my system I get this message

[17179574.032000] Kernel Panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send report. Then try booting with 'noapic' option [17179574.032000]

I would like to know if anyone can tell me what this means and how to fix it

---

### Post by louis_nichols on 2007-03-07
It means you have to disable apic. You just need to follow instructions:

At the grub boot screen, select your default kernel and press "e". Then go to the line containing the kernel parameters and press "e" again. go to the end of the line and add *noapic *there. Then press ENTER to confirm and "b" to boot. This should get your system started.

Once logged in, open for edditing the file /boot/grub/menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```

Here, go to every line containing the word kernel and add *noapic *at the end. Then save and close and you should be all set. Well, at least until the next kernel update, because this resets your menu.lst file and you have to make the modification above again.

---

### Post by jrandolph on 2007-03-07
how do i know which one to select there is 4 of them

---

### Post by amishone on 2007-03-07
I am getting the same error when I try to install.

From what I have found on other sites, it appears to be a problem that is related to CPU and/or motherboard (I have an AMDx2 Windsor AM2 and an ASUS M2N32-SLI Deluxe). Vista installed without a hitch, so I'm sure Ubuntu can too. Right? :)

What are your processor and mb jr?

---

### Post by jrandolph on 2007-03-07
I have an AMD Athlon 64x2 with an ASUS M2N4 SLI mobo

---

### Post by amishone on 2007-03-07
Does anyone have any insight into this problem? Is there a connection between the ASUS mobo/AMD 64x2 chip and this Kernel Panic error?

Should I try a different distro?

Any suggestions?

Danke!

---

### Post by rccharles on 2007-03-07
> **jrandolph said:**
> how do i know which one to select there is 4 of them

I'd pick the one closed to :
Ubuntu, kernel 2.6.15-23-386
It is also the first entry.

You wouldn't want:
Ubuntu, memtest86+
This tests your memory. Of course it wouldn't hurt to check out your memory.

Robert

---

