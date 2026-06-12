---
title: "Disabling IRQ #7"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-07-02
I've installed ubuntu on my laptop (had to set noacip and nolapic options at boot), and it seems to run okay for a while. However, after a few minutes I get a message:

Message from syslogd
kernel: disabling IRQ #7

what is happening here? (I haven't been able to figure out what stopped working :) ) and how do I avoid this?

---

### Post by Pragmatist on 2007-07-02
This person has the same problem, and solved it with a BIOS setting:
[http://ubuntuforums.org/showthread.php?t=354257&highlight=disabling+IRQ](http://ubuntuforums.org/showthread.php?t=354257&highlight=disabling+IRQ)

---

### Post by Cypher on 2007-07-02
The reason for the Kernel disabling a particular IRQ is when an interrupt is generated on a IRQ which contains no Interrupt Handlers.

All modern OS' uses a heirarchy of Interrupt Handlers for any given IRQ by which when a hardware generates an interrupt, the first interrupt handler (ISR) is called, if it determines that the interrupt was from a device it knows/cares/handles, then it deals with the interrupt and tells the OS so. If that device the ISR cares about didn't generate the interrupt, it simply passes it along and along until it reaches the OS. If the OS gets an unhandled interrupt, it is deemed a "Spurious interrupt" and is usually accompanied by the comica l "IRQ X: Nobody cared" message. To prevent any breakage of system or instability, the IRQ is disabled.

In MOST cases, this is usually a good/safe thing. However, sometimes with faulty ISR or hardware, a valid device's IRQ gets disabled leading to failure.

Is any particular device in your system failing to function after this message or does everything continue to work like it always did???

---

### Post by EvilBro on 2007-07-03
> **Cypher said:**
> Is any particular device in your system failing to function after this message or does everything continue to work like it always did???
I've yet to discover what has failed, so I guess I'm safe for now. BTW thanks for the extra info, it helps a new user like me to get to grips with what is happening under the hood.

---

### Post by EvilBro on 2007-07-24
> **EvilBro said:**
> I've yet to discover what has failed, so I guess I'm safe for now.
And I'm no longer safe, meaning I've discovered what no longer works: All usb-ports. They stop functioning after the irq 7-message. Note that if I have a device plugged in, they keep working (until I remove the device, then they will still crash after a few minutes with the same irq 7- message). How do I prevent this from happening?

---

### Post by Pragmatist on 2007-07-24
> **Pragmatist said:**
> This person has the same problem, and solved it with a BIOS setting:
[http://ubuntuforums.org/showthread.php?t=354257&highlight=disabling+IRQ](http://ubuntuforums.org/showthread.php?t=354257&highlight=disabling+IRQ)
Did you try this?

---

### Post by EvilBro on 2007-07-25
> **Pragmatist said:**
> Did you try this?
The BIOS options on my hp dv6137eu is very limited (I hadn't looked at it before, but I was actually surprised about how little you can adjust). The option spoken of in the link is not available to me.

I did try booting with 'irqpoll' added to menu.lst. This did indeed stop the usb-ports from crashing. I haven't been able to discover a downside yet to this approach (although I do have the idea that sometimes the system 'halts' briefly). What does the 'irqpoll' option do exactly?

---

### Post by Pragmatist on 2007-07-25
[http://ubuntuforums.org/showthread.php?t=468228](http://ubuntuforums.org/showthread.php?t=468228)

---

### Post by ozzyprv on 2007-12-11
Having the same problem after installing 7.04 on my laptop (HP dv9005ca).

> 
"Message from syslogd@Mybox at Mon Dec 10 21:58:47 2007
Mybox kernel: [   229.146442] Disabling IRQ #7


another time it was 

> 
"Message from syslogd@Mybox at Mon Dec 10 21:58:47 2007
Mybox kernel: [   197.251709] Disabling IRQ #7


I tried going into the BIOS (Pragmatist's post), but disabling the PnP is not among the  the FEW options.

Any help?


> **Pragmatist said:**
> This person has the same problem, and solved it with a BIOS setting:
[http://ubuntuforums.org/showthread.php?t=354257&highlight=disabling+IRQ](http://ubuntuforums.org/showthread.php?t=354257&highlight=disabling+IRQ)

---

