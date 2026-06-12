---
title: "Irq"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by saximus on 2007-08-20
Hello,

I installed Ubuntu Studio a while ago and I am trying to figure some things out. I am having some problems with my sound and I am trying to find out what the reason might be. 

I had problems with irq 18. In order to get ubuntu started at all, I had to use a command called 'irqpoll'

Could someone please tell me what IRQ refers to and what the command 'irqpoll' does?

---

### Post by A3sthetix on 2007-08-21
IRQ: [http://en.wikipedia.org/wiki/Interrupt_request](http://en.wikipedia.org/wiki/Interrupt_request)

To my knowledge, an IRQ allows the computer to communicate with specific hardware componants. Each item (sound, modem, etc) has an unique IRQ. 

From what I gather (logically) the irqpoll command will check IRQs to see what componants are behind specific IRQs. If a componant is not behind the standard IRQ, you might have problems booting up.

Try adding the IRQFIX command to your boot-up parameters.

---

