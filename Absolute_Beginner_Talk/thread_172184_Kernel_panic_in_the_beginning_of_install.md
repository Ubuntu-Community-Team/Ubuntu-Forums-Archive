---
title: "Kernel panic in the beginning of install"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by ponytail on 2006-05-08
ok

i try to install ubuntu 5.10 on my msi s250 laptop

it goes fine till it asks to press enter or type server.. so quite in the beginning..
then it loads for a while, prints a lot of numbers and "Kernel panic - Not syncing: attempted to kill init"

thats it, i have to restart..

i think someone here might know whats the problem.. 

thanks

---

### Post by Sendervictorius on 2006-05-08
It could be a lot of thngs - hardware related - memory, CDROM, motherboard,., or just some hardware wierdness the Kernel doesn't know how to deal with. Could also be a corrupt install CD. 

The message basically means the init process tried to die, but init isn't allowed to die, so the Kernel paniced.

The panic routine adds text to the front of the message telling you more about what the system was actually doing when the panic occurred. This is where the "not syncing" part comes from. panic tries to issue a sync system-call to push all buffered data out to the hard-disks before it goes down.

The second part of the message is what was provided by the original call to panic(). For example, we find panic("Tried to kill init!") in kernel/exit.c.

When you see this message - the cause of the actual failure will be found in the startup messages immediately preceding this one. This is often the case with kernel-panics. init encountered something "really bad," and it didn't know what to do, so it died, so the kernel died too.

So, please post the messages before the panic message, and lets see if we can work out what the problem is.

---

### Post by mulvila on 2007-01-08
> **ponytail said:**
> ok

i try to install ubuntu 5.10 on my msi s250 laptop

it goes fine till it asks to press enter or type server.. so quite in the beginning..
then it loads for a while, prints a lot of numbers and "Kernel panic - Not syncing: attempted to kill init"

thanks

You need to set noapic option in the boot. I do not quite know what it is, but worked with mined.

---

