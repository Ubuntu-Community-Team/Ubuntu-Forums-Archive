---
title: "Quick question, I hope it's not too stupid..."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Keyper7 on 2007-06-30
Hi,

Just one curiosity: should I expect that, in future versions of Ubuntu, I won't need
extra kernel parameters (ex: noapic) to boot as I need now? I'm not sure if this is
a "will be eventually fixed" kind of problem or "hardware is to blame, what is
happening is actually the correct behavior" kind of problem.

Sorry if I'm being too naive here.

Thanks in advance,
-Keyper7

---

### Post by Stephen Howard on 2007-06-30
Those kernel options tend to be there to cater for buggy hardware or bios, so most will stay for many years.  You can perhaps compile a kernel after customising it for your hardware?

PS:  I assume you're not typing in the kernel parameter each time, but have incorporated it into the grub boot block?

---

### Post by Keyper7 on 2007-06-30
Hi Stephen, thanks for the answer.

Yes, I edited the menu.lst, so the parameter typing itself is not a burden. :)

What bothers me the most, though, is the feeling that I can just choose the
"less unpleasant" situation: without parameters I have a unstable system
with USB 2.0 and perfect suspend and hibernate, but that occasionaly
hangs while using, or even during the initial boot. With noapic, I lose
USB 2.0 capabilities and get kernel panic on suspend/hibernate. Adding
noirqdebug gives my USB 2.0 back, but also causes the second core to
be 60% busy handling hardware interrupts and does not solve the suspend
and hibernate problems.

(on the other hand, I've heard here and there that the USB problem might be
caused by a buggy ehci_hcd module and the suspend/hibernate problem
might be caused by buggy nvidia drivers... if that's the case I think there's
more hope for a solution in a near future, right?)

So now I'm curious about compiling my own kernel... By doing it, can I have
more hope of finding a perfect solution or will I hardly do much more than
disabling apic by default, for example?

Thanks in advance,
-Keyper7

PS: I'm using an HP Pavilion DV6258SE, I think it's worth mentioning in case
someone knows a solution for my issues... ;)

---

