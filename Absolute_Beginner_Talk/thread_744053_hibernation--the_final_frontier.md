---
title: "hibernation--the final frontier"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by stubblepoo on 2008-04-03
i have moulded my ubunt to (pun intended) exactly what i want in every respect except for one. my hibernation still doesnt work. you select the hibernate button and it starts, goes black for a few secs then boots right up again, the hd never even stops spinning. i have been through all other similar post and tried everything but nothing changes it. i have an enabled swap drive of 251mb called linux-swap in Gparted. could anyone give me a checklist of things to check and fix. this is the last hurdle for me so all help is appreciated.

---

### Post by PriceChild on 2008-04-03
How much ram does your machine have?

What video card are you using, are you using any binary drivers?

---

### Post by stubblepoo on 2008-04-03
i have 512 ram and an nvidia go 5200 card and i don't know what a binary driver is, so maybe?

---

### Post by PriceChild on 2008-04-03
You need a swap partition larger than the amount of ram you are using to be able to hibernate. (the ram gets written to the swap, to be resumed from later.)

If you really want to be able to hibernate, you could boot into a live cd and resize the partitions, however you will need to find out the new UUIDs and edit your /etc/fstab before the system will boot again.

---

