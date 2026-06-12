---
title: "LiveCd wont boot up."
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by AaronSmith on 2006-05-15
Okay so first time trying linux, my friend ended up with alot of Ubuntu cd's and he was kind enough to give me a 64bit one.

Okay so i thought great ill just pop the live cd to see if its worth installing. So i pop the live cd in and then i reboot. The ubuntu screen comes up and says press enter to boot, so i press enter.

The kernel console writing comes up lots of writing and then it gets stuck and a few lines above says.

16.953819   ACPI: Looking for DSDT in initrd.... Not found! 

So next time i rebooted i looked through the help and found a command 

live acpi = off 

so i tried that and i got alittle further only this time another error msg on the kernel console came up.

28.0600112: Initializing Cryptographic API
28.060105: Pcie_portdrv_probe -> Dev [5a37:1002] has invalid IRQ check vendor BIOS.

So i thought damn what do i do now.

After a couple of attempts i come across a command.

noapic nolapic  something to do with disabling bugging ACPI?

i type live noapic nolapic and then the console whizzs lots of lines of code and then it looks like its working things seem to be going then i get  blank screen. I thought oh its booting from a cd so ill just give it 30mins. Nothing came up the cd light came up every so often.

Anyways theres my dilemma.

Has anyone come across this or knows what is happening.

Any help would be appreciated.

---

### Post by MaximB on 2006-05-15
maybe it's b/c you are using the ubuntu 64 version and your machine doesnt support it.
try the i386 version dvd/cd

---

### Post by AaronSmith on 2006-05-15
Hmm then the manufacturers have ripped me off then :D

I mean my computer is an AMD Turion 64, thats why i got 64bit instead of 32bit.

---

### Post by 5-HT on 2006-05-15
What about trying 'irqpoll' or 'pci=noacpi' as boot options?

---

### Post by AaronSmith on 2006-05-16
Nope didnt work :(.

---

