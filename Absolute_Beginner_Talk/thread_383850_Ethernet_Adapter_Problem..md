---
title: "Ethernet Adapter Problem."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Hawkz Skylord on 2007-03-13
Hello. Well, I think i got a really big problem.

I bought a Ethernet Adapter, Realtek RTL8139. I'm using windows XP, this card IS working pretty fine on it. But, I tried to change to Ubuntu. I installed it but when I was going to configure the internet, the card was not installed by the system.

I searched at Google for a solution. I typed **lspci **on the console to find my card. But, I found "Unknown Device" on the Ethernet Adapter Topic. And the card code was 1904, thats not the Realtek one.

*0000:00:0f.0 Ethernet controller: Unknown device 1904:8139 (rev 01) *

Anyway, i keep looking for a solution, and I found a website who says that my Card is not Original.

So, How can I install the driver of this card ? I guess my card "is" a Silan SC92031 PCI Fast Ethernet Adapter.

I really want to migrate to Ubuntu. Please help me.

---

### Post by lloyd_b on 2007-03-13
Could you post the output from the "lshw" command?  Not the entire list (it'll be pretty long) but just any section involving "ethernet" or "unclaimed".  We need a better idea as to what ethernet card you have.

Lloyd B.

---

