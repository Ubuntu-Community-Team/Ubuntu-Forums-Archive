---
title: "unbale to boot LIVECD"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-03-28
Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option

I get this when I try to boot from a 6.10 Live CD on a new AMD X2 5200+ on Gigabyte SLI mobo. I have installed XP OK but cannot get the live CD to run to install it.
 
 
Need help please!

---

### Post by mahy on 2007-03-28
Looks like Ubuntu doesn't work with ACPI on your motherboard. Have you tried booting it with the 'noacpi' option as suggested?

---

### Post by tchoklat on 2007-03-28
how do I do this from the livecd?

---

### Post by leo antony on 2007-03-28
Hello, 

I had to add "live acpi=off" to the 'other options'. I also deleted splash and quiet. 

If you get the live cd to work, then install, you may have to add "pci=noacpi" to boot up from your hd. 

This is what worked for me. Hope it helps.

---

### Post by tchoklat on 2007-03-28
still unsure as I cannot write to the live CD to modify anything!

---

### Post by NicoleM on 2007-03-28
once the splash screen comes up there should be a number of function options at the bottom of the screen.  F6 will be something like "edit boot parameters" or something similar.  when people are telling you to input the commands, they intend for you to do so in the line that comes up upon hitting F6

---

### Post by tchoklat on 2007-03-28
sounds like it, I will give it a go

thanks

nicolem

---

