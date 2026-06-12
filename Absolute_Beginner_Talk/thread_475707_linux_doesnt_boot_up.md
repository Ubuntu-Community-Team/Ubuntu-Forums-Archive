---
title: "linux doesnt boot up"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by kvorion on 2007-06-16
I have a strange problem. My linux kernel does not boot. When I select either one of the two ubuntu versions installed on my machine, it starts to load the kernel and simply stays there.....it does not go ahead.......I have ubuntu 5.10 and xubuntu 6.10 installed on my machine.
I realized that this problem started after I got my RAM changed although I dont know if that is the reason behind the problem. One thing to note is that my winxp boots and works as before. The strange thing is that I cant boot even from a live cd.......
I tried doing a memtest.....it ran for something like 30 mins after which I got bored and switched off...it did not show up any errors till then.

Please help me get my linux box working again......

---

### Post by FleetAdmiral74 on 2007-06-16
Hmm, does it freeze halfway through the boot process? Exactly how far do you get, like you select the button and nothing after that at all? any text?

---

### Post by kvorion on 2007-06-20
I select the ubuntu OS....hit enter......

It shows Ok loading kernel........and then nothing......it stays there......no further text...no kernel panic....nothing..

---

### Post by kvorion on 2007-06-20
I edited the boot params and removed quiet and splash....
It showed me a couple of messages and ended here....

ACPI: PCI Interrupt 0000:01:00.0 -> GSI 18 (level, low) -> IRQ 169
(Xubuntu 6.10)

For Ubuntu 5.10.....the message was very similar except for a different IRQ.

Any clues?

Update: My friend suggested that I try adding acpi=off to the boot params.....but nothing happened there either......

---

### Post by kvorion on 2007-07-04
Anybody?

---

### Post by Cappy on 2007-07-04
Try boot param:
noapic nolapic

You might want to also try switching the RAM sticks?

---

