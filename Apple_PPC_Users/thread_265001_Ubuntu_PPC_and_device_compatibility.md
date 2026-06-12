---
title: "Ubuntu PPC and device compatibility"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by discosammy on 2006-09-25
I bought a usb tv device (ATI XCLAIM TV).

It's only compatible with OS 9, not OS 10.

The question, would it work with PPC Linux?

Any guesses? From previous learnings, hardware not mac compatible, has no chance with Linux PPC.

But if it's just a software driver, is there a chance? Any suggestions or advice?

---

### Post by discosammy on 2006-09-28
I know you-all are out there. I can hear you breathing!

Is my question so obvious, I should have found the answer myself? Or is all you learn-ed folk stumped?

I'm going to give it the college try once it arrives.

---

### Post by stmiller on 2006-09-29
Philips chipset tv cards are all supported by Linux. You'd have to find out what the chipset is on the card.

> Any guesses? From previous learnings, hardware not mac compatible, has no chance with Linux PPC.

Not true. Linux and Mac OS X are completely different operating systems. What they support/don't support doesn't depend on one another. For Linux, it just depends if the hardware manufac has released specs for the device where a group of volunteers could then write a Linux driver.

---

### Post by discosammy on 2006-09-29
> Not true. Linux and Mac OS X are completely different operating systems. What they support/don't support doesn't depend on one another. For Linux, it just depends if the hardware manufac has released specs for the device where a group of volunteers could then write a Linux driver.

That's not what I read in this forum. I was hoping that by using ubuntu i could get a soundblaster live in a PowerMac to work under the logic you used above.

this is the reply I got:

 
I still don't think you could install a PCI card into a Mac without it already having Mac support.

PCs use a startup system called a BIOS. Macs use a system called Open Firmware, which (among other things) registers PCI cards with the computer. If the card doesn't have specific compatibility with Open Firmware, it cannot be made available to the computer.

full thread: [http://www.ubuntuforums.org/showthread.php?t=235967](http://www.ubuntuforums.org/showthread.php?t=235967)

---

### Post by confusimo on 2006-09-30
Sorry just a quick question.  All philips chipset tuners are linux compadible?  Or just some philips?  I have 64 bit 6.06 on a pc.  Any tuner with philips chipset will do?  Any philips number?

---

### Post by 3rdalbum on 2006-09-30
I wrote the message you linked to, and I was just going by what I'd heard from someone else. I've never tried putting cards into a Mac.

However, the situations are different. A PCI card registers itself with Open Firmware, but a USB device definately does not.

Are you running PPC Linux already?

---

### Post by discosammy on 2006-09-30
I tried getting ubuntu going on my powermac, but the install kept crashing. then i stumbled across this xclaim tv device and i'm thinking of trying again.

i don't know squat about the pci architecture. if i get ubuntu going i may try the sb live card.

i've no idea about the chipset. wish me luck.

---

