---
title: "ubuntu on AMD?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-03-08
I posted earlier about dual booting xp and ubuntu, but thats far from my current problem. I cant even get a liveCD to work on my hp dv6000z, with an amd chipset. I downloaded the cd specifically for amd's, checked the disc data in MD5sum and in the cd's menu. The loading screen seems to freeze everytime I try. It goes from the gray loading bar, to a neon green one which remains in the same position for up to 20 minutes. I dont know what the problem is. maybe it takes longer. if anyone has any experience with this situation, please respond. thanks a lot

---

### Post by Bachstelze on 2007-03-08
If your CPU is an AMD but is not 64 bit capable, the "amd64" CD will not work. Download the "i386" one.

---

### Post by Chopperman on 2007-03-08
> **em11488 said:**
> I posted earlier about dual booting xp and ubuntu, but thats far from my current problem. I cant even get a liveCD to work on my hp dv6000z, with an amd chipset. I downloaded the cd specifically for amd's, checked the disc data in MD5sum and in the cd's menu. The loading screen seems to freeze everytime I try. It goes from the gray loading bar, to a neon green one which remains in the same position for up to 20 minutes. I dont know what the problem is. maybe it takes longer. if anyone has any experience with this situation, please respond. thanks a lot

All three laptops I have tried do the same thing without a boot hint. nothin to do with the cpu. try hitting F6 on the boot menu and add "noapic" to the end of the command line presented

---

### Post by em11488 on 2007-03-08
what would noapic do? im just curious, I know this forum is very helpful and full of smart people, but i just want to make sure doing this stuff wont mess up my current sytem

---

### Post by Chopperman on 2007-03-08
> **em11488 said:**
> what would noapic do? im just curious, I know this forum is very helpful and full of smart people, but i just want to make sure doing this stuff wont mess up my current sytem

I totally missed the bit about AMD (I'm tired) but yeah it depends on 32bit vs 64bit. I have tried both...I recommend the 32bit(386) over the 64 for offering the least trouble in getting used to this system (I am pretty new myself). Re: NOAPIC - as far as I understand it, the APIC is an advanced form of IRQ (interrupt requests) and something in linux isnt playing well with it and so that is the instruction to not try to use it.  Of course I could be totally wrong :)  At any rate, NOAPIC did the trick on my compaw presario(s) and the HP DV9000.

---

### Post by em11488 on 2007-03-08
where do I download the 32 bit version, all I see is the 64 bit version for amd.

---

### Post by Chopperman on 2007-03-08
> **em11488 said:**
> where do I download the 32 bit version, all I see is the 64 bit version for amd.

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

just click the link for the server closest to you and then click the link for desktop/laptop pc

---

### Post by Levitation on 2007-03-09
I tried "noapic" "nolapic" seperately and together. This was at the Boot prompt (after pressing F6). It said something like "image not found". What can I do to get the Live CD to run? I am using 5.10
I just ordered 6.06 will that be any better? Should I try 6.10?

Thanks

---

### Post by doubtful wisdom on 2007-03-09
Many of us run AMD processors, most of them are 32 bit.  Use the i386 ISO.

---

### Post by goofeyfoot on 2007-03-09
I have a 64 version and run it on an AMD 64.  I had the same problem and here is what I found.  The system did not like my cd rom for some reason.

On closer inspection, I found that I had the cdrom on a sata controller.  That was complicated further by the fact that the cdrom was not natively sata.  It was a regular ide and I just used a converter controller card so I could use the sata connection.

The hard drive for ubuntu was on a regular ide controller.

For some reason, that completely blocked the install.  I don't know why.

So I pulled off the sata card and just made the whole thing plain vanilla.  I ran the ubuntu drive as the master and the cdrom as the slave.  Both were on one ide ribbon cable.

For some reason, that worked like a charm.  So, you might try to move the hardware around like I did.

By the way I am a new guy to this so I can't be more scientific than to say it worked for me.

Also get ready for a real sleigh ride.  This linux is pure torture for anyone who doesn't program computers for a living.  Maybe once I get everything up and running I will feel differently.  Right now, I am pretty cynical.

Michael

---

### Post by dptxp on 2007-03-10
I am a very recent Linux user, and I think that Windows has tortured me quite a bit. Every new stuff needs a bit of understanding.

---

