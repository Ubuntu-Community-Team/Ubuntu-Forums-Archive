---
title: "Help, CD will not boot correctly."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by chrisu87 on 2007-03-10
I burned the ISO to a cd and I get the menu, however when I try to boot I run into a problem.

The screen goes black, white text scrolls down the screen, and it usually stops on some numbers in brackets [xxxx.xxxxx] or something of that sort, and my machine stops there.

I've got about 760 MB RAM, and a 2.93 GHz Celeron D Processor.

Anyone have any advice?

Thanks a million for your help,
Chris

(oh, and I do have an older pressed cd that a friend gave to me, however it will not boot either.)

---

### Post by rsambuca on 2007-03-10
Try entering some of these as boot options (F6 at the menu)
```
ide=nodma
```
If that doesn't work, try adding all of this to the boot options```
irqpoll pci=noacpi noapic nolapic acpi=off
```

---

### Post by honns on 2007-03-10
have you verified the integrity cd?

---

### Post by Kateikyoushi on 2007-03-10
If neither of the CDs will boot it is very likely to be hardware related, try to give us more information about the hardware for example what motherboard do you use ?

---

### Post by chrisu87 on 2007-03-10
I've checked the CD, and got 0 errors.

Thanks for the replies, I appreciate them.

I tried both commands, and neither of them worked :(.

I tried booting the CD normally again and some of the text on the screen looked important so I jotted it down.

"[17179622.16000] BUG: unable to handle kernel paging request at virtual address fffffee8"

Thanks again,
Chris

---

### Post by chrisu87 on 2007-03-10
> **Kateikyoushi said:**
> If neither of the CDs will boot it is very likely to be hardware related, try to give us more information about the hardware for example what motherboard do you use ?


I'm not sure about the motherboard, it's a Compaq Presario.

---

### Post by Kateikyoushi on 2007-03-10
First test your memory with the CD, if it is good then ,try to install from the alternate CD.

---

### Post by chrisu87 on 2007-03-10
Did both of those, fell asleep and the install failed :(.

---

### Post by chrisu87 on 2007-03-11
I used CPU-Z and found out my motherboard's model

Manufacturer: ASUSTek Computer Inc
Model: Guppy

I really want to run Linux on here, so I appreciate the help.

---

### Post by chrisu87 on 2007-03-12
Anyone have any advice???? I'm really looking forward to trying out Ubuntu for the first time, but so far it's been difficult.

---

