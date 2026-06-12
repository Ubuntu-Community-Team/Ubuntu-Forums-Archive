---
title: "What does noapic means?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2007-06-05
When I install Ubuntu in my computer I have to use this option.
The first time I installed Ubuntu I was having problems and someone suggested that option, after hitting F6 and then typing 'noapic' it worked!

But I don't know what noapic means and why do I have to use it in my machine.

Can anyone please tell me the meaning of this installing option and why my computer doesn't work without it.

Thanks in advance

---

### Post by yabbadabbadont on 2007-06-05
It prevents the kernel from trying to use the APIC hardware.

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

---

### Post by dunklegend on 2007-06-06
Thanks yabbadabbadont

So maybe I have to put the noapic option because it's from Intel, and my processor is an AMD
Athlon X2 3800+.

Am I right?

---

### Post by yabbadabbadont on 2007-06-06
It is most likely because support for your particular APIC hardware is buggy or incomplete in the kernel at this time.  Ten kernel releases from now, or even the next one, it may work fine.  Hardware support in Linux is sometimes tricky.

---

### Post by dunklegend on 2007-06-06
Thank you! :D

---

