---
title: "Hardware diagnostic tool"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by bentonian on 2007-12-12
Is there a tool that will tell me exactly what hardware I've got? I just picked up a used PCI video card, and I want to know the chipset and memory. Thanks!

---

### Post by sourcemorph on 2007-12-12
go to the terminal and execute "lspci" 

alternativelyyou can install a software called "sysinfo" from add/remove programs.

---

### Post by rfruth on 2007-12-12
Eyeball the 'new' PCI video card - only way to be sure :)

---

### Post by bentonian on 2007-12-13
Many thanks for the feedback.

I have tried lspci, but it doesn't give hardware information, like how much VRAM is on the card.

What do you mean, "eyeball" the card? How can I tell how much memory is on it?

---

### Post by rfruth on 2007-12-13
Eyeball = visual inspection --  for example my ATI x300 video card has a small paper label on it with lots of info or (google) search for x300, there is more info than I want or I can run lshw and see there is 128 MB of VRAM
[http://docs.google.com/Doc?id=ajgsz8nqvtv3_201c6s9mv]("http://docs.google.com/Doc?id=ajgsz8nqvtv3_201c6s9mv")

---

